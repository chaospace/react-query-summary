# react와 react-query를 사용후기

- query요청에 사용되는 파라미터는 가능한 최소로 유지한다.

```javascript
/**
     query 요청에 필요한 파마리터가 여러가지라도 특정 키를 기준으로 요청 시 구할 수 있다면
     요청시 해당 키를 만들어 queryKey롤 지정해 사용.
    @param key1:string   // 쿼리 키
    // key1를 바탕으로 함수 내부에서 만들어서 사용되는 변수
    @param key2:sring    // 검색 종료 일
    @param key3:string   // 검색 대상
    @param key4:string   // 검색 타입( 일간, 월간, 연간 )
*/
const useRequireQuery(key1:string) => {
    const key2 = key1+10
    const key3 = key2+30;
    const key4 = key3-'22';
    return useQuery( [queryKey, key1, key2, key3, key4], queryFunction, options );
}

function MyComponent(){
    const [queryParams, setQueryParams] = useState(20);
    const {dat, isLoading} = useRequireQuery(queryParams);
}
```

- select를 통한 데이터 가공 시 가능하면 원본 reponse가 가진 key를 변환을 처리하도록.
