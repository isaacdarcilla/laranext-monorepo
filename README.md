<h1 align="center" id="title">Laravel + Next monorepo starter ⭐</h1>

<p  align="center" id="description">Based on the Laravel Breeze scaffolding with NextJS</p>

### Installation Steps

Clone the repository

```
git clone https://github.com/isaacdarcilla/laranext-monorepo
```

Install node packages

```
cd laranext-monorepo
npm install
```

Install composer packages</p>

```
cd backend
composer install
```

Migrate database</p>

```
php artisan migrate --seed
```

Next, ensure that your application's `APP_URL` and `FRONTEND_URL` environment variables are set to `http://localhost:8000` and `http://localhost:3000`, respectively.

After defining the appropriate environment variables, you may serve the Laravel application using the serve Artisan command:

```
cd backend
php artisan serve

or 

cd laranext-monorepo
npm run start -w @mono/backend
```

Finally, run the application via `npm run dev`. The application will be available at `http://localhost:3000`

```
cd frontend
npm run dev

or 

cd laranext-monorepo
npm run dev -w @mono/backend
```

> You may want to open separate terminals for `backend` and `frontend` folders. Or you can just use `-w <package>` flag when starting the development server.

### Adding Package to Workspace

To add new packages to the workspace, for example `husky`,

```
npm install <dependency> -w <package>
npm install husky -D -w @mono/frontend
```

### Authentication Hook

This Next.js application contains a custom `useAuth` React hook, designed to abstract all authentication logic away from your pages. In addition, the hook can be used to access the currently authenticated user:

```js
const ExamplePage = () => {
    const { logout, user } = useAuth({ middleware: 'auth' })

    return (
        <>
            <p>{user?.name}</p>

            <button onClick={logout}>Sign out</button>
        </>
    )
}

export default ExamplePage
```

> Note: You will need to use [optional chaining](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining) (`user?.name` instead of `user.name`) when accessing properties on the user object to account for Next.js's initial server-side render.

### Named Routes

For convenience, [Ziggy](https://github.com/tighten/ziggy#spas-or-separate-repos) may be used to reference your Laravel application's named route URLs from your React application.

### More Info

https://github.com/laravel/breeze-next/tree/master
