# C# Selenium "How to automate a Facebook Post on FB page"

using OpenQA.Selenium;
using OpenQA.Selenium.Chrome;
using System.Threading;


class EntryPoint
{
    static IWebDriver driver = new ChromeDriver();
    static IWebElement textBox;




    static void Main()
    {

        //TestPage URL

        string url = "https://www.facebook.com/login/?next=http://testpage.com";
        driver.Navigate().GoToUrl(url);

        //Login using the Test FB credentials
        textBox = driver.FindElement(By.Name("email"));
        textBox.SendKeys("uid");

        textBox = driver.FindElement(By.Name("pass"));
        textBox.SendKeys("Pw");

        driver.FindElement(By.Id("loginbutton")).SendKeys(Keys.Enter);

        //Test Post and Post Button

        driver.FindElement(By.Name("xhpc_message_text")).SendKeys("This a Test Post generated by the Automated Script");
        Thread.Sleep(5000);
        driver.FindElement(By.XPath("//button/span[.=\"Post\"]")).Click();

        //Wait
        Thread.Sleep(3000);
        driver.Quit();
    }


}
