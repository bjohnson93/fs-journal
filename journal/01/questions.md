# Foundations of Web Development
01. In your own words, why do we use Git?
    > We use Git to track changes made to our code every time we commit, this way we can go back to previously committed code that we may want to use. It is also so that multiple developers can work on different portions of a project at the same time.

02. In the terminal, what is the command `mkdir` used for?
    > "Make Directory" or to make a new folder

03. What is a ***pseudo-class*** and what are some of the most common ones you think you will use?
    > A pseudo class applies styling on an element with a specific requirement, like with hover- when you hover over the element you can apply a specific value for that action.  I think ones that will be commonly used are :before, :hover, :after, :required

04. What is ***specificity*** and how might you use it to your benefit?
    > Specificity is essentially priority of how css is applied to an element, depending on whether you use the element selector, a class, or an ID, they each hold a different value/strength. This is useful when you want to target the  body text to be one color or font, but maybe some areas you want to stand apart within the body you can style with a class selector and it will change just those classes. id's being the highest can be especially useful with javascript, and ID is very unique, where classes can be applied to many elements.

05. What problems do you think you could run into if you over-utilized the `!important` feature?
    > It would be difficult to diagnose issues in your css as !important overrules other css rules. If i wanted to overrule and still use it, I'd have to do so with another !important.

06. What are the three components that makeup a `CSS` rule? <br> Example:

    ```css
        h1 {
            color: rgba(255, 210, 33, .75);
        }
    ```

    > Selector > Property > Value

07. How do you think good design influences people when visiting a website, and what sorts of things could you convey through design alone?
    > Good design not only can make things look visually appealing, but also user friendly. If something is easy to use, people are more likely to use it and recommend it. There are colors that portray things like love, health, money- whatever you are trying to attract the user with. Good design can make the content seem more trustworthy to the user as well.

08. What is the purpose of ***wireframing***?
    > To be able to present a mock-up of what something is going to look like, like a rough draft before you actually start coding- that helps you achieve the desired layout.

09. Do you think wireframes are worth the time, energy, and effort that they require? Why or Why not?
    > Yes, I think it would help you keep your eyes on the big picture, and is easier to "chunk" things up to eventually get the desired look.

10. Define the display `:flex property:`
    > This allows the item to grow or shrink within a flex box- so it doesn't necessarily hold one static value.

11. What `CSS` properties affect the size of a box model?
    > Content, Padding, Border, Margin
