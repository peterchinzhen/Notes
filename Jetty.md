# Patterns when creating Java web project 
## Main class
- Filter (javax.servlet.Filter)
- Handler
- Router

##　Details
- Filter
  Filter is a class which we could communicate with the container or sevlet
 
 1. void	init(FilterConfig filterConfig)  
  Web コンテナは、Filter をサービス状態にするために init メソッドを呼び出します。
> note: use init to generate a router entity. 
    
 2. void	doFilter(ServletRequest request, ServletResponse response, FilterChain chain)  
  Filter クラスの doFilter メソッドはコンテナにより呼び出され、最後のチェーンにおけるリソースへのクライアントリクエストのために、 毎回リクエストレスポンスのペアが、チェーンを通して渡されます
> note: use doFilter to make router genenate handler and do handle some request
  
 3. void	destroy()  
  サービス状態を終えた事を Filter に伝えるために Web コンテナが呼び出します。
- Handler
Handler is a class that we defined to make handle request and response more easily
      

