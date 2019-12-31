#SeleniumWebDriverFramework

A maven Selenium framework that is built which allows Spring to manage dependency via dependency injection.

Open a terminal window/command prompt
Clone this project.
CD into project directory
mvn clean verify
_All dependencies will be downloaded and specific driver executable dependencies are already installed in project directory

##What I Should do to run my test

_To run any unit tests that test your Selenium framework you just need to ensure that all unit test class contains Spring test annotation

@SuppressWarnings("SpringJavaAutowiringInspection")
@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration(classes=BeanConfig.class)
public class Test {
....
}
You don't need to do this:
WebDriver driver=new WebDriver()
To create a WebDriver instance :
@Autowired
private WebDriver driver
A webDriver object will be wired automatically
Note: You can name your test class whatever you want.

##Further Information

-Dbrowser=firefox
-Dbrowser=chrome
-Dbrowser=ie
-You don't need to download the IEDriverServer, or chromedriver binaries, they are already added to the project directory


Inorder to run any specify environment and please use below commands for example to run on test environment
mvn clean verify -Denv=test -Ptest

Currently I have used (data.properties) as the environment configuration file so you can run the project by below command
mvn clean verify -Denv=env -Ptest

##Selnium Grid
To run the code with Selenium Grid, you will need to specify the URL of the selenium hub

Example command: 

test environment
mvn clean verify -Denv=test -Premote

development environment
mvn clean verify -Denv=dev -Premote

Currently I have used (env.properties) as the environment configuration file so you can run the project by below command
mvn clean verify -Denv=env -Premote

If Hub url is different to default
mvn clean verify -Denv=test -DfailIfNoTests=false -Dhub huburl

Tests will run in parallel on a per feature file basis. e.g. 4 features will result in 4 nodes running in parallel on the grid.