# FB login system with ReactJS

## Instalation


```shell
npm install react-facebook-login 
```

## Usage

```js
import React, { Component } from 'react'
import FacebookLoginBtn from 'react-facebook-login'


export default class LoginFacebook extends Component {
    state = {
        auth: false,
        name: '',
        picture: ''
    }

    componentClicked = () => {
        console.log('fb clicked')
    }

    responseFacebook = (response) => {
        console.log(response)
        this.setState({
            auth: true,
            name: response.name,
            picture: response.picture.data.url
        })
    }

    render () {
        let facebookData
        this.state.auth ?
            facebookData = (
                <div>
                    <img src={this.state.picture} />
                    <h1>{`Hi ${this.state.name}`}</h1>
                </div>
            ) : 
            facebookData = (
                <FacebookLoginBtn
                appId="1112476095779315"
                autoLoad={true}
                fields="name,picture"
                onClick={this.componentClicked}
                callback={this.responseFacebook} 
                icon="fa-facebook"
                />
            )


        return (
            <>
                {facebookData}
            </>
        )   
    }
}

```