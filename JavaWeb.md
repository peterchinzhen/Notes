# Patterns when using filter
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
      

# Patterns when using servlet
javax.servlet.httpServlet  

1. protected  void	doDelete(HttpServletRequest req, HttpServletResponse resp)  

2. protected  void	doGet(HttpServletRequest req, HttpServletResponse resp)

3. protected  void	doHead(HttpServletRequest req, HttpServletResponse resp)  

4. protected  void	doOptions(HttpServletRequest req, HttpServletResponse resp)  

5. protected  void	doPost(HttpServletRequest req, HttpServletResponse resp)  

6. protected  void	doPut(HttpServletRequest req, HttpServletResponse resp)  
 
7. protected  void	doTrace(HttpServletRequest req, HttpServletResponse resp)  

8. protected  long	getLastModified(HttpServletRequest req)  

9. protected  void	service(HttpServletRequest req, HttpServletResponse resp)  
           public で定義された service メソッド経由で標準 HTTP リクエストを受け取り、それらをこのクラスで定義された doXXX メソッドにディスパッチします。
10. void	service(ServletRequest req, ServletResponse res) 


