# Prisma

### Filtering on the existence of a one-to-many relation

``` javascript
// to find records that do have at least 1 relation
where: {
  relation: { some: {} }
}
// to find records that don't have any relations
where: {
  relation: { none: {} }
}
```

### Case-insensitive filtering

```javascript
const users = await prisma.user.findMany({
  where: {
    email: {
      equals: 'prisma.io',
      mode: 'insensitive', // Default value: default
    },
  },
})
```