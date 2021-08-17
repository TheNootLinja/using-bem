# BEM (Block Element Modifier)
BEM is a widely used methodology of writing CSS. 

## When SHOULDN'T you use BEM?
BEM really only shines when you have a more complex webpage or application as it is made to help keep styling from clashing when you have a ton of elements that you would otherwise have to keep track of what classes you are using for certain items and not accidentally naming something else further along by the same class name.

## Tips & Tricks
- SCSS makes using the BEM system a lot easier as you have the ability to write your css as shown in the code block below. SCSS allows you to just write out the card selector once at the top level, then just use & in place of that selector from there on out inside of that original block started with the selector. This keeps things much more clean and makes it so you don't have to continually repeat yourself with the top level selector over and over again. But the fun doesn't stop with nesting 1 level deep. No no no. If you look inside the &__item selector you will see that I also am able to nest the active modifier we created inside as well.
``` css
.card {
	padding: 0 5em;
	
	&__img {
		display: block;
		height: 100px;
		width: 100%;
		background: #e0466b
	}
	
	&__content {
		padding: 1.5em;
		background: white;
	}
	
	&__list {
		list-style-type: none;
		display: flex;
		margin: 0;
		padding: 0;
	}
	
	&__item {
		padding: .3em .5em;
		margin-right: .5em;
		background: rgb(230,230,230);
		border-radius: .3em;
		font-size: .85em;
		
		&--active {
			background: #d4d4d4;
			font-weight: bold;
		}
	}
	
	&__link {
		background: #2c8973;
		color: white;
		text-decoration: none;
		padding: .5em 1em;
		border-radius: .5em;
		display: inline-block;
		margin-top: .5em;
		
		&:hover {
			background: #267764;
			
		}
	}
}
```

## Block
- A standalone entity that is meaningful on its own.

## Element
- A part of a block that has no standalone meaning and is semantically tied to its block.
## Modifier
- A flag on a block or element. Use them to change appearance or behavior.

There are many reasons for using it such as:
- It helps avoid issues with specificity
- It helps with styling organization and readability (if the user knows BEM)

## Example breakdown
So let's say you have built a card element for displaying information. Inside that card you have child elements such as a picture, a title, a short description, and a button. In this case, the block would be the card (class='card'). Then when you move down to one of the child elements you would use a class name such as: 
- picture: class='card\__picture'
- title: class='card\__title'
- description: class='card\__description'
- button: class='card\__button'

Then, lets say you want to have a class that is applied to the button when it is active. That would be where the modifier section of BEM comes in. The class would look like:
- class='card\__button card\__button--active'
``` js
	<div class="card card--active">
		<img src="www.something.com" class="card__picture">
		<h1 class="card__title">title</h1>
		<p class="card__description">description</p>
		<button 
		class="card__button card__button--active"
		>
		Click Me
		</button>
	</div>
```

The above code is for the simple card element that I mentioned and in this case, I have 2 modifier classes. The first is on the actual card element which we would use if we had multiple cards and wanted the one the user is currently interacting with to have different styling from the others on both the button and the card itself.

