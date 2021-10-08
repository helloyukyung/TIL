Navigation.js add

## logout 된 후 다시 home으로 돌아갈 수 있도록 해보자 

- 1<Redirect>
기본적으로 from , to 가 존재  
마지막에 넣음 
<Redirect from="*" to ="/"/>
이 경우 모든 route가 다 "/"로 redirect 됨 
이 "/"route에 있으면 상관이 없는데 그 외의 route로 가게 되면 /(top)으로 돌아가가게끔 함 

- 2 <usehistory>
router를 hook으로서 사용

 const history = useHistory();
history.push("/") 

