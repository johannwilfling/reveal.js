# TDD & BDD
## Test Driven Development
## Behavior Driven Development

<small>
[Johann Wilfling](johann.wilfling@gmail.com) / [@johann.wilfling](@johann.wilfling)
</small>

---

# TDD

Software-Entwicklung Prozess / Vorgehensweise

- Initial (failing) test case
- (Minimum) amount of code to pass the test
- Refactor (to acceptable standards)

<br/>

## Red - Green - Refactor

--

# Key-Element von TDD?

--

# Existenz von Tests

## Psychologischer "Life hack" / "Dev hack" <!-- .element: class="fragment" -->
Wie bringe ich Entwickler dazu, Tests zu schreiben? <!-- .element: class="fragment" -->

--

# Vorteile von TDD

### Outside > In
### Refactoring
### Dokumentation
### Verbessert die Architektur?
Meist (DHH) <!-- .element: class="fragment" -->

--

## Wirkliche Grund

![](tests_nie_nachher.jpg)

---

# BDD

<blockquote>
BDD is a second-generation, outside-in, pull-based, multiple-stakeholder, multiple-scale, high-automation, agile methodology.
</blockquote>
<small>
(en.wikipedia.com)
</small>

--

Eng verbunden mit

## User Stories
<blockquote>
As a [role] I want [feature] so that [benefit]
</blockquote>

<br/>
## Acceptance scenarios
<blockquote>
Given [initial context], when [event occurs], then [ensure some outcomes]
</blockquote>


---

HIStory <!-- .element: class="h1-lower" -->

## [T|B]DD - Test first

<br/>

Ich bin ein gl&uuml;hender [T|B]DD Fan - schreibe ich alle Software 'test first'?
#Nein <!-- .element: class="fragment" -->

--

# Development Flows
## (or personal style?)

- Defined input-output
- Creative

---

<!-- .slide: data-background="#007777" -->

# Very Good Example
## (Defined input output)
### News parser 
### (Rails)

--

<!-- .slide: data-background="aau_news.png" -->

--

<!-- .slide: data-background="#007777" -->

## News parser (Rails)

* Kein RSS / Atom verf&uuml;gbar
* "Bad quality" HTML
* Unterschiedliche Konstellationen

<br/>

* Immer dieselben Testf&auml;lle
* Manuelles Tippen auf der Console (&ouml;d und langsam)
    
<pre><code class="ruby"> 
    >> html_string = '<div class="spalte122"><p> 18.Juli 2014 </p></div>'
    >> date = NewsParser.parse_date_from(html_string)
    >> date
    ' 18.Juli 2014 '
    >>
</code></pre>    

--

<!-- .slide: data-background="#007777" -->

## &Ouml;d und langsam VS. Tests

<pre><code class="ruby"> 
  context "with a fake html response" do

    before(:each) do
      html_fixture = File.read(File.join('spec', 'fixtures', 'uninews.html'))
      UninewsItemParser.any_instance.stub(:fetch_remote_document).and_return(html_fixture)
    end

    context "parse an uninewsitem correctly" do
      let (:uninews_item) { parser.fetch_items.first }
    
      it "parses the title" do
        expect(uninews_item[:title]).to eq "&Ouml;sterreichische ..."
      end

      it "parses no date if first paragraph is a text" do
        expect(uninews_item[:date]).to eq ""
      end

      it "parses the description with no date" do
        expect(uninews_item[:desc]).to eq "Vom 15.-17. April 2013 ..."
      end

</code></pre>    

---
<!-- .slide: data-background="#4d7e65" -->

# Ohlala Example
## (Creative)
### News Application
### (iOS)

Rookie & Frameworks

- iOS SDK, UIKit, Objective-C <!-- .element: class="fragment" -->
- XCTest <!-- .element: class="fragment" -->
- Outside-In: UIAutomation | bwoken <!-- .element: class="fragment" -->
- Outside-In #2: Frank, calabash, (KIF) <!-- .element: class="fragment" -->
- BDD: Kiwi, Specta, Expecta <!-- .element: class="fragment" -->

--
<!-- .slide: data-background="#4d7e65" -->

## Red - Green - Refactor
## (Nachdenken) - (Test schreiben) - (Implementieren)

<blockquote>
  Teste ich das Richtige? 
</blockquote>

* ".. tableView should contain 100 entries .." ?
* iOS Segue (Storyboard)
* Architektur als Hinderniss? (DHH)

--

<!-- .slide: data-background="extreme-abstracting.jpg" data-background-size="800px" -->

---

# Good Example
## (Abstract input-output)
### Verwaltungs- und Managementapps (CRUD)
### (BDD, Java)

* User-Stories und Scenarios
* Arbeiten mit externen Stakeholdern
* Beschreibung des erwarteten Verhaltens der Applikation

--
Textliche Szenarien mit Stakeholdern erarbeiten

<pre><code class="gherkin"> 
  Feature: Account Registierung an der AAU
  
  Scenario: Account aktivieren
  
  Given ich habe mich beim Bewerbungsportal registriert
  And ich aktiviere den Link in der Best&auml;tigungsemail
  Then sollte ich auf der Account aktivieren Seite sein
  And ich w&auml;hle den ersten Usernamen in der Liste
  And ich setzte mein Passwort
  And ich klicke auf Aktivieren
  Then sollte ich eine Aktivierungsemail erhalten
  And ich sollte auf der Success Seite sein
</code></pre>    


---

TDD, BDD, DDD, SODD .. ?

Egal: 

# TESTING!

--

* Frameworks sind kein Silver Bullet (DHH)
* Nicht alles ist "creative" ;-)
* Refactor
* Sicherheitsnetz und das Vertrauen auch "legacy" Code anzugreifen

--

<!-- .slide: data-background="#8c4738" -->

## A fool with a tool is still a fool!

--
<!-- .slide: data-background="#007777" -->

## Guides / Tipps

* TDD / BDD Lernen 
  * die Applikation wird besser verstanden
* TDD Tools lernen
  * Simple as possible
  * Opinionated Frameworks (Rails)
* Mocks & Stubs vermeiden
* BDD (Cucumber) nur f&uuml;r Stakeholder
  * zus&auml;tzlicher Layer f&uuml;r Developer
  * (Cucumber > Capybara > (Selenium) > Rspec > Testlogik)

--
<!-- .slide: data-background="#4d7e65" -->

## Guides / Tipps #2

* Testen, was Sinn macht
* Test-Metriken nicht beachten 
  * CI-Server in der Nacht
* St&ouml;rungen des PM nicht beachten
  * "You get paid for writing code!"
  * Wasserfall hat noch nie funktioniert

--

<blockquote>
  A year from now you'll wish you'd started today
</blockquote>

<br/>

# Testing

<!-- .slide: data-background="#8c4738" -->


<!-- Nice background colors
mint: #007777
green: #4d7e65
red: #8c4738
 -->
