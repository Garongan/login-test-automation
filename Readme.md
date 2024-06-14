## Login Testing automation using java and selenium
### if you're using javascript use this code

### first check your node and npm
```bash
node -v
npm -v
```

### install selenium
```bash
npm install selenium-webdriver
```

### create login.js file and copy this code
copy this code is for testing login using chrome browser

```javascript
const { Builder, Browser, By, Key, until } = require('selenium-webdriver')

;(async function example() {
    // set driver
    let driver = await new Builder().forBrowser(Browser.CHROME).build()
    try {
        // hit the login url
        await driver.get('https://example.domain.com/login')
        // send value to login form
        await driver.findElement(By.id('user_email_Login')).sendKeys('example@gmail.com', Key.RETURN)
        await driver.findElement(By.id('user_password')).sendKeys('password', Key.RETURN)
        // trigger the login button
        await driver.findElement(By.name("login")).click();
        await driver.wait(until.titleIs('Example - Home'), 1000)
    } finally {
        await driver.quit()
    }
})()
```