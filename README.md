


## `Error de validación de datos`
_Handler.php_
```php
    protected function convertValidationExceptionToResponse(ValidationException $e, $request) {
        if($e->response) {
            return $e->response;
        }

        return $this->invalidJson($request, $e);


    }

    public function invalidJson($request, ValidationException $e) {
        return response()->json([
            'message' => $e->getMessage(),
            'errors' => $e->errors(),
        ], $e->status);
    }
```
`Creacion de request para hacer la validación`
```bash
php artisan make:request Auth/RegisterRequest
```