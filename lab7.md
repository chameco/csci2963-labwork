On Reliquary Development
------------------------
Last week, I changed Reliquary's internal error-handling to use a flatter monad transformer stack.
In order to simplify the codebase, an eventual goal is moving away from MTL towards applicative functors, which compose nicely.
I also gutted the old REPL, as it felt clunky and uninformative, and much of the code surrounding it was written when I was significantly less experienced with surrounding issues.
The plan is currently to simplify the current environment/namespace system, and then finish a higher-level ADT implementation using that new system.
