# Shīkensu

> シーケンス    
> Sequence

Run a sequence of functions on in-memory representations of files.  
__Build static websites with ease__, without conforming to a specific structure.

### Markdown example

```gren
import Bytes exposing ( Bytes )
import Shikensu
import Shikensu.Contrib as Shikensu
import Shikensu.Definition as Shikensu
import Shikensu.Focus as Shikensu exposing ( Focus(..) )
import Shikensu.Path as Path
import Task


main : Shikensu.Program
main =
    -- 🚀
    Shikensu.program sequence CurrentDirectory


sequence : Shikensu.Task -> Shikensu.Task
sequence task =
    task
        |> Task.map (Shikensu.withExtension "md")
        |> Task.andThen Shikensu.read
        |> Task.map
                (\bundle ->
                    bundle
                        |> Shikensu.renameExtension "md" "html"
                        |> Shikensu.permalink "index"
                        |> Shikensu.renderContent renderMarkdown
                )
        |> Task.andThen (Shikensu.write destination)


destination : Shikensu.Focus
destination =
    Relative (Path.directory [ "build" ])


renderMarkdown : Shikensu.Definition -> Maybe Bytes
renderMarkdown def =
    Maybe.map renderMarkdownBytes def.content
```