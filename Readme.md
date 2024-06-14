## Login Testing automation using java and selenium
### select branch fro another programming language
### run locally

#### clone this repo

```bash
git clone https://github.com/Garongan/login-test-automation.git
```

#### open the directory

#### install dependency

```bash
mvn install
```

#### run the login test

```bash
mvn clean test
```

#### or

copy this code is for testing login using chrome browser

```java
package org.example;

import io.github.bonigarcia.wdm.WebDriverManager;
import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.Assertions;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;

public class LoginTest {

    WebDriver driver;

    @BeforeEach
    void setup() {
        driver = WebDriverManager.chromedriver().create();
    }

    @AfterEach
    void tearDown() {
        driver.quit();
    }

    @Test
    public void login() {
        // set property from chrome driver
        driver.manage().window().maximize();

        // hit the login url
        driver.get("https://example.domain.com/login");

        // get html element
        WebElement userEmailLogin = driver.findElement(By.id("user_email_Login"));
        WebElement userPassword = driver.findElement(By.id("user_password"));
        WebElement loginButton = driver.findElement(By.name("login"));

        // send the data to login form
        userEmailLogin.sendKeys("example@gmail.com");
        userPassword.sendKeys("password");

        loginButton.click();

        String actualUrl = "https://example.domain.com/home";

        String expectedUrl = driver.getCurrentUrl();

        Assertions.assertEquals(expectedUrl, actualUrl);
    }
}
```