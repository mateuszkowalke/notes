# NestJS

### To configure graphql playground, add this to your GraphQLModule.forRoot config

``` javascript
playground: {
	settings: {
		'request.credentials': 'include',
	}
}
```

This particular setting sets the default request.credentials to 'include'.