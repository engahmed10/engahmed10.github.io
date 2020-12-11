---
layout: post
title:      "Final project using Redux-React and Rails Api"
date:       2020-12-11 06:11:23 +0000
permalink:  final_project_using_redux-react_and_rails_api
---

React without redux make our project more complicated because every time you should pass props to another component, that's tough. By using react with redux, we will be able to easily manage the state and behavior of the state to organize projects and fix bugs quickly.
In this project, I used a third-party API to fetch data. The idea of this project users can search for any book they want and can see the detail of the book, including title, author, price, year published, and ISBN on both sides of the book card frontside and backside. The admin also has individual books on the main page and has a comment option, so the user replay with the comment to each book, and the user can see other user's comments. Still, it can not change other user's comments, and only he can change his own comment, delete or update comment.
We used the jwt JSON web token for authentication so user can auto login after signup and login. Brower will save that token in his localStorage, and when reopening in the web page in the same browser, will autologin. Also, localstoreage help me to pass the token to the backend and decoded to find user_id

```
token=params[:localStorage]["token"]
token=JWT.decode(token, 'my_s3cr3t', true, algorithm: 'HS256')
user_id = token[0]["user_id"]
```

The trick in this project I got was getting an error when trying to display all comments,i was receiving empty comment=[] , because i put all comments in componentDidMount() lifecycle method when component first mount should receive all comments if there is any comment

```
componentDidMount(){

         this.props.fetchComments()

}
```

after i reviewed deeply and i followed step by step then i figured out the issue was state appears before fetch complete his process because fetch working asynchronously, so the state was receiving from redux store before receive fetch the response from backend or promise is pending
.For solving this issue, I used if statement to check if comment received or not yet (undefined )
```
if (this.props.comments && this.props.comments.length ){ 
 .....
}
```
for update comment, i added toggle variable to my state editform and assign it to default value false,so when clicking on the edit button, each comment editform will change to true and will render update form, and hidden comment add form

```
{ this.state.edithform ?
              <form className="commentForm" >
                    <h5>Update Comment</h5>
                    <input type="textarea"  name="description" onChange={(e)=>this.handleChange(e)}  className="commentFormInput"/>
                    < button className="commentButton"  onClick={(e)=>this.handleUpdate(e)} > update comment</button>
               </form>

        :      
                <form className="commentForm" onSubmit={(e)=>this.handleSubmit(e,book_id)} >
                            <h5>Replay With Comment</h5>
                            <input type="textarea"  name="description" onChange={(e)=>this.handleChange(e,book_id)} className="commentFormInput"/>
                            <input type="submit"  className="commentButton" />
                </form>

         }
```
we got benefit from other rect lifecylce methods like componentWillUnmount()
 ```
componentWillUnmount() {
        this.props.resetState({type:"RESET_STATE"})
  }
```
, so after you use the search bar and books changed when you navigate to other routes, the state will reset,and when you come back to same page, you will see admins books , because we have that fetches all books when mounting again
```
componentDidMount(){

     this.props.fetchBooks()
  }
	
```
Conclusion
We build our full-stack bookstore app,in the front end, we used react ,redux java script libraries with other features like html and css react-router-dom to navigate between different components .aslo we used jwt web token with localstorage in both front end and backend to add authentication to our apps.In backend, we just used two-part of MVC just controller, Model,beside we used the database to store our data and all users data,we didn't need part view because we did our view in front end , we used Ruby on Rails language to controller our data in API/v1/controlellr and we used active record association has many and belongs to asscociation in our models to connect between two models,finaly we added some data to our seed file from third parties data base .


