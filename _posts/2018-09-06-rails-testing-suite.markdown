---
layout: post
title:  My 2018 Rails Testing Setup
date: 2018-09-06 13:22:00
description: Behavior Driven Development is cool
image: /assets/img/posts/rails-testing-2018/cucumber-screenshot.png
social: true
tag: programming
relatedposts: true
---

<div class="">
    <img class="col three" src="{{ site.baseurl }}/assets/img/posts/rails-testing-2018/cucumber-screenshot.png" alt="" title="Rspec for unit testing"/>
</div>

2018 has been a big year for me. I picked up some real experience with an internship in web development. I went to Europe. I got to partake in shooting a documentary in Prague. I learned about the beauty of pizza nachos. And I finally decided to start testing my code.

Yeah, I know pretty crazy. As a staunch supported of [cowboy coding][cowboy-coding], the move to actually planning and writing good code (whatever that means) was a difficult one. But as I started to take Rails development seriously, I quickly realized the importance of writing good tests. In fact, it was after internship project that didn't involve any tests that I realized just how great tests are. Seriously, it sucks merging in code from a bunch different branches and then realizing something broke somewhere and you're spending the rest of your day digging through branches to find out what exactly broke that you realize you want to write tests.

With that said, writing tests is boring. Very boring. It's basically saying, "I am going to create this really cool feature, but first let me list out every single part of it instead of actually writing it". It also gets pretty intimidating when you run your tests and see everything fails. Sure, its because you haven't even written the feature out, and once you start most will be passing without much work. Still, seeing 20 some failing tests is scary.

All that said, I'm pretty excited by the testing suite we've created at my internship and that I'm starting to use on my personal projects. At its core, our process is Behavior-Driven-Development (BDD). [You can read more about BDD here][wikipedia-bdd], but at its core, BDD is a process led by both the business development and developer team (which in the case at both my internship and personal projects, is me). It involves writing a series of "behaviors" and interactions that a person may make with a project, and what the outcome should be in these cases. Hopefully, it'll make more sense soon.

### Cucumber


<div class="">
    <img class="col three" src="{{ site.baseurl }}/assets/img/posts/rails-testing-2018/Real-Cucumber-800x416.jpg" alt="" title="A tasty veggie, cucumber is also the glue that holds together of all my tests"/>
</div>
<div class="col three caption">
    A tasty veggie, cucumber is also the glue that holds together of all my tests.
</div>

[Cucumber][cucumber] is probably my favorite part of my Rails testing suite because it makes writing tests almost fun. Cucumber allows you to write "features", ie interactions a user will make with your website, in plain english. Cucumber uses a few key words like 'Given', 'When', and 'Then' to give these features some structure. Each of these keywords is used in a scenario, which is a general description of what task the user is performing. Each of these scenarios is put inside a .feature file, which is just a collections of scenarios that involve some common feature. 

A great example is authentication. An authentication.feature file contains scenarios that all involve authentication in some way, shape or form. Here's an example:

{% highlight bash %}

Feature: Authentication
     In order to use the website
     As a user
     I should be able to sign up, log in and log out
     I should be told when sign up, log in, and log out fails

Scenario: User signs up with valid credentials
     Given I visit the homepage
     When I fill in the sign up form
     And I confirm the email
     Then I should see that my account is confirmed


Scenario: User logs in with valid credentials
     Given I am a registered user
     And I visit the homepage
     When I fill in the log in form
     Then I should be logged in


Scenario: User logs out
     Given I am a registered user
     And I am logged in
     And I visit the homepage
     When I click the log out button
     Then I should be redirected to the log in page

{% endhighlight %}

The above snippet shows just how simple writing a feature file is, but its not even the best part of cucumber. In a rails environment, you can run the command `rake cucumber`, and cucumber will convert these features into a series of "steps" that help you break apart a feature and write a test for each component. The result for the "User logs in with valid credentials" scenario will look like this:

{% highlight ruby %}

Given("I am a registered user") do
  pending # Write code here that turns the phrase above into concrete actions
end

When("I fill in the log in form") do
  pending # Write code here that turns the phrase above into concrete actions
end

Then("I should be logged in") do
  pending # Write code here that turns the phrase above into concrete actions
end

{% endhighlight %}

At this point, you can fill the steps in with the necessary code to perform the feature. The next time you run `rake cucumber`, it will show which tests are running and succeeding. 

### RSpec


<div class="">
    <img class="col three" src="{{ site.baseurl }}/assets/img/posts/rails-testing-2018/rspec.png" alt="" title="Rspec for unit testing"/>
</div>
<div class="col three caption">
    RSpec for unit testing.
</div>

[Rspec][rspec] is the next major component of my testing suite, and probably where I spend most of time in Rails projects. It's official website says it's "Behaviour Driven Development for Ruby. Making TDD Productive and Fun." I'm not entirely sure it makes Test Driven Development fun, but it sure makes it a hell of a lot easier. 

This is especially true in Rails when using the scaffolding feature. RSpec auto generates unit tests for the controllers, model, and views of your newly scaffolded feature. What's neat is that most of these files are already auto-populated with tests for different controller functions and views, like index and show. It's up to you to fill in some of the blanks so that the tests succeed.

After scaffolding a new feature, RSpec is used for Test Driven Development. It makes things especially convenient in the model specs, where you can test for the existence of certain columns, relationships, data formats, and other neat stuff. The real power however, comes from Shoulda Matchers, another gem that takes RSpec to the next level.

## Other Tools

### Shoulda Matchers


<div class="">
    <img class="col three" src="{{ site.baseurl }}/assets/img/posts/rails-testing-2018/shoulda-matchers-.svg" alt="" title="Shoulda Matchers Logo"/>
</div>
<div class="col three caption">
    One-liners that test common Rails functionality.
</div>

[Shoulda Matchers][shoulda-matchers] is what puts the "fun" (or better yet, simplicity) into RSpec. Shoulda Matchers' website claims it "provides RSpec- and Minitest-compatible one-liners that test common Rails functionality", and I couldn't agree more. Shoulda Matchers turns long lines of test like this:

{% highlight ruby %}

describe User do
  it 'is not valid if its username is the same as another user within the same account' do
    _existing_user = FactoryGirl.create(:user,
      username: 'johnsmith',
      account_id: 1
    )
    user = FactoryGirl.build(:user,
      username: 'johnsmith',
      account_id: 1
    )
    expect(user).not_to be_valid
  end

  it 'is valid if its username is the same as another user within the same account, but for different case' do
    _existing_user = FactoryGirl.create(:user,
      username: 'johnsmith',
      account_id: 1
    )
    user = FactoryGirl.build(:user,
      username: 'JohnSmith',
      account_id: 1
    )
    expect(user).to be_valid
  end
end

{% endhighlight %}

Into this:

{% highlight ruby %}

describe User do
  context 'validations' do
    before { FactoryGirl.build(:user) }

    it do
      should validate_uniqueness_of(:username).
        scoped_to(:account_id).
        case_insensitive
    end
  end
end

{% endhighlight %}

In my code, they've turned testing model relations and column validations from several lines each to one liners. I still do use some multi line tests for more complex behaviors, Shoulda-Matchers not only makes tests more readable; it makes them easier to write. Gone are the days of writing 5 or 6 multi line tests that all fail all because of some syntax error inside them. More lines of code = higher chance of a bug, and Shoulda Matchers takes of this.

### FactoryBot

According to [FactoryBot's readme][factorybot], "factory_bot is a fixtures replacement with a straightforward definition syntax, support for multiple build strategies (saved instances, unsaved instances, attribute hashes, and stubbed objects), and support for multiple factories for the same class (user, admin_user, and so on), including factory inheritance."

In much, much simpler terms, FactoryBot is a super convenient way to set populate the database for tests.

{% highlight ruby %}

FactoryBot.define do
  factory :user, aliases: [:host] do
    name "MyString"
    email "MyString@MyString.com"
    password "MyString"
  end
end

{% endhighlight %}

FactoryBot also has a couple of neat tricks up its sleeve. For example, if you need to make a relationship between models your generating, you can create an alias like the above called :host. Then, in another factory that needs a relationship to host, you can write:

{% highlight ruby %}

association :host, factory: :host

{% endhighlight %}

FactoryBot will automatically create a database entry for "host" using the :user factory which is aliased as :host. 

### Database Cleaner

[Database Cleaner][databasecleaner] is a gem that sets up a series of strategies for "cleaning", or resetting, the database in between tests. With just the following lines of code:

{% highlight ruby %}

RSpec.configure do |config|
  config.before(:suite) do
    DatabaseCleaner.strategy = :transaction
    DatabaseCleaner.clean_with(:truncation)
  end
  config.around(:each) do |example|
    DatabaseCleaner.cleaning do
      example.run
    end 
  end
end

{% endhighlight %}

Cleaning the database is important because you never want any of your tests to be reliant on modified data. Relying on modified data is just a huge headache, and minor changes to a controller or model could make all your tests fail when in actuality they should be passing. Database Cleaner just simplifies the process of resetting the database between tests, and consequentially, makes your life easier.

[cowboy-coding]: https://en.wikipedia.org/wiki/Cowboy_coding
[wikipedia-bdd]: https://en.wikipedia.org/wiki/Behavior-driven_development
[cucumber]: https://www.google.com/search?q=cucumber+bdd&oq=cucumber+bdd&aqs=chrome..69i57j69i60l2j0l5.3265j0j4&sourceid=chrome&ie=UTF-8
[rspec]: http://rspec.info/
[shoulda-matchers]: https://github.com/thoughtbot/shoulda-matchers
[factorybot]: https://github.com/thoughtbot/factory_bot
[databasecleaner]: https://github.com/DatabaseCleaner/database_cleaner