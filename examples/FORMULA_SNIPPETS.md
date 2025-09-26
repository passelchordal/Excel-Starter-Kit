
# Example Formula Snippets (Plain Text)

## N-th Largest Unique Value
=LAMBDA(array,n,
  LET(u,SORT(UNIQUE(array),,-1),IF(n<=ROWS(u),INDEX(u,n),NA()))
)

## Unique Values Sorted by Frequency (descending)
=LAMBDA(array,
  LET(u,UNIQUE(array),
      f,MAP(u,LAMBDA(x,COUNTIF(array,x))),
      TAKE(SORTBY(HSTACK(u,f),SEQUENCE(ROWS(u)),,-1),,1))
)

## Filter by Multiple Criteria (AND)
=LAMBDA(range,crit1,crit2,
  FILTER(range,(crit1)*(crit2))
)

