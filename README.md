# RunMyNotes.jl

I like to write up notes of how to use my packages in plain `.jl` files,
which the package [Literate.jl](https://github.com/fredrikekre/Literate.jl) can run,
producing `.ipynb` notebooks, with graphs embedded.
This little package automates that slightly. Typing this:  
```
folder("~/.julia/dev/MyPackage/notes/")
```
or (roughly) equivalently
```
import MyPackage
package(MyPackage)
```
will run all files in that folder.
Then it will convert the resulting notebooks to `.html`
to make it easier to preview last week's graphs, unless you say `html=false`.
You can also pass `all=false` to update only files that have changed. 

By default everything is saved in the same folder,
but to avoid saving for all eternity every day's versions of all figures etc,
I add to `.gitignore` these lines:
```
.DS_Store
*.ipynb
*.html
```
Then I can happily include this in the package's tests, it returns `true` if there are no errors.
In fact if you type `] test RunMyNotes` this will happen for this package itself,
for a simple [note.jl](notes/note.jl). Or else: 
```
using RunMyNotes
package(RunMyNotes, "~/Desktop")
```

Michael Abbott, December 2018
