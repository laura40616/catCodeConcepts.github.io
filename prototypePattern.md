## Prototype Pattern explained…with cats

![Prototype Pattern](./images/prototypeCat.jpg?raw=true)



One of my favorite books that my mom would read to me as a child was [“Millions of Cats”](https://en.wikipedia.org/wiki/Millions_of_Cats) by Wanda Gag. In the book, an old couple is lonely and the wife decides that she wants a cat. The old man sets out on a quest to find a cat for his wife. He searches far and wide and eventually finds a hill covered in cats! To quote the book, “there were hundreds of cats, thousands of cats, millions and billions and trillions of cats”!!! (exclamation marks are my own) The old man couldn’t decide which cat to take home, so he took all the cats home 😬 The end of the book is…interesting. You’ll have to find out what happens at the end on your own!

The prototype pattern made me think of this book. I think the old man would have had a much easier time if he had some code! The prototype pattern creates new objects without having to make a new one from scratch. Think about our Cat class. It’s a pretty simple class, but in the real world sometimes classes can have a lot in them and it can be time consuming and hard on resources. What if in the story all the old man had to do was call .clone() on the Cat object? He could have hundreds of cats, thousands of cats, millions and billions and trillions of cats in no time! What a time saver!

The prototype pattern has an interface which defines the clone() function, a class that implements the interface, and a client that will use the class and create the copies.

```
class Cat implements CatPrototype {
    private name: string
    constructor (name: string) {
        this.name = name
    }
    meow () { console.log('Meow!'); }
    clone(): Cat {
        const catClone = Object.create(Cat.prototype)
        catClone.name = this.name
        return catClone
    } 
}

interface CatPrototype {
    clone(): CatPrototype
}

(()=> {
    const binx: CatPrototype = new Cat('Binx')
    console.log('binx', JSON.stringify(binx))
    const binxClone = binx.clone()
    console.log('binxClone', JSON.stringify(binxClone))
    
    const kitkat: CatPrototype = new Cat('Kitkat')
    console.log('kitkat', JSON.stringify(kitkat))
    const kitkatClone = kitkat.clone()
    console.log('kitkatClone', JSON.stringify(kitkatClone))
})()

// output
// binx {"name":"Binx"}
// binxClone {"name":"Binx"}
// kitkat {"name":"Kitkat"}
// kitkatClone {"name":"Kitkat"}
```
