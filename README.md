# PlotlySave

Package to implement PlotlyBase together with a save function independently of [PlotlyJS](https://github.com/sglyon/PlotlyJS.jl).



## Installation

```julia
using Pkg
Pkg.add("https://github.com/hhaensel/PlotlySave")
```
or
```julia
]add https://github.com/hhaensel/PlotlySave
```


## Usage

PlotlySave reexports PlotlyBase so it is sufficient to do
```julia
using PlotlySave

p1 = Plot(scatter(x=1:10, y=2:11))
save("test.png", p1)
```

This package might become part of JuliaPlots, therefore it is not (yet) registered.

## Background

Kaleido has for long been a part of PlotlyBase but has recently been removed, due to non-availability on some platforms and due to extra loadtime (more information, e.g. [here](https://github.com/sglyon/PlotlyBase.jl/issues/52)).
In order not to interfere with the current version of PlotlyJS this package exports `save` from FileIO with inverted order of filename and plot compared to savefig. If you want to use old scripts with existing savefig commands, you can import it via:
```julia
import PlotlySave.savefig
```

## Future

There is a branch [`hh-abstractplot`](https://github.com/hhaensel/PlotlySave#hh-abstractplot) that plays together with respective branches in my forks of `[PlotlyBase](https://github.com/hhaensel/PlotlyBase#hh-abstractplot)` and [`PlotlyJS`](https://github.com/hhaensel/PlotlyJS#hh-abstractplot) to introduce an `AbstractPlot` type that both `Plot` and `SyncPlot` are subtypes of. That way many mutltiple definitions can be avoided and other projects could derive their own subtypes.

For this to happen `PlotlySave` would probably need to move to [`JuliaPlots`](https://github.com/JuliaPlots/PlotlyJS). Therefore, this package is currently not registered.

Feel free to use the [issue pages](https://github.com/hhaensel/PlotlySave/issues) to comment or improve this approach.


