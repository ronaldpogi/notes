# Best Design Patterns in Laravel





## Repository Pattern

* Separates business logic from data access.
* Example: Instead of directly querying models inside controllers, use a UserRepository.

```php
// App\Repositories\UserRepository.php
class UserRepository {
    public function allActive() {
        return User::where('active', 1)->get();
    }
}
```
```php
// App\Http\Controllers\UserController.php
class UserController extends Controller {
    public function index(UserRepository $repo) {
        return $repo->allActive();
    }
}
```
Makes testing easier and code more maintainable.





## Service Pattern

* Keeps business logic in dedicated service classes.
* Example: Handling payments:

```php
// App\Repositories\UserRepository.php
class PaymentService {
    public function process(User $user, float $amount) {
        // handle payment gateway integration
    }
}
```
```php
// Controller
$paymentService->process($user, 100);
```
Keeps controllers slim.





## Dependency Injection

* Laravel’s IoC container automatically resolves dependencies.
* Instead of creating new instances manually, type-hint dependencies in constructors.
```php
class OrderController extends Controller {
    public function __construct(private PaymentService $paymentService) {}

    public function store(Request $request) {
        $this->paymentService->process(auth()->user(), $request->amount);
    }
}
```
Promotes loose coupling and testability.





## Observer Pattern

* utomatically listen for model events like created, updated, deleted.
```php
// App\Observers\UserObserver.php
class UserObserver {
    public function created(User $user) {
        Mail::to($user->email)->send(new WelcomeMail());
    }
}
```
```php
// AppServiceProvider.php
User::observe(UserObserver::class);
```
Keeps model logic clean.





## Strategy Pattern
* Good for interchangeable algorithms (e.g., multiple payment gateways).
```php
interface PaymentStrategy {
    public function pay(float $amount);
}

class PaypalPayment implements PaymentStrategy {
    public function pay(float $amount) { /* PayPal logic */ }
}

class StripePayment implements PaymentStrategy {
    public function pay(float $amount) { /* Stripe logic */ }
}
```
```php
// Service
class PaymentService {
    public function __construct(private PaymentStrategy $payment) {}
    public function process(float $amount) {
        return $this->payment->pay($amount);
    }
}
```
Easy to switch providers without touching main business logic.





## Factory Pattern
* Use Laravel Factories to generate models for testing/seeding.
```php
User::factory()->count(10)->create();
```
Saves time in testing and database seeding.





## Command Bus / CQRS
* Use Jobs & Commands for handling complex workflows.
* Example: php artisan make:job ProcessOrder
* Each job handles one responsibility.





## Summary:
* Best Practices → Keep controllers thin, use services, repositories, queues, validation, policies, caching.
* Best Patterns → Repository, Service, Observer, Strategy, Factory, Dependency Injection.





## License
[MIT](https://choosealicense.com/licenses/mit/)
