# query 초기화

====

```ts
const queryClient = useQueryClient();

const handleLogout = async () => {
  await queryClient.invalidateQueries(queryKeys.user);
  await deleteAuth();
  await router.replace("/");
  // ...other logic
};
```

파라미터로 넣어준 쿼리키에 해당하는 쿼리를 명시적으로 stale 하다고 알려주고, 해당 쿼리 데이터를 새로 refetching 해준다.
