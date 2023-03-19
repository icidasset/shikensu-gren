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
    [ ".."
    , "example"
    , "content"
    ]
        |> Path.directory
        |> Relative
        |> Shikensu.program sequence


sequence : Shikensu.Task -> Shikensu.Task
sequence =
    Task.map (Shikensu.withExtension "md")
        >> Task.andThen Shikensu.read
        >> Task.map
                (\bundle ->
                    bundle
                        |> Shikensu.permalink "index"
                        |> Shikensu.renameExtension "md" "html"
                        |> Shikensu.renderContent renderMarkdown
                )
        >> Task.andThen (Shikensu.write buildDir)


buildDir : Shikensu.Focus
buildDir =
    [ ".."
    , "example"
    , "build"
    ]
        |> Path.directory
        |> Relative


renderMarkdown : Shikensu.Definition -> Maybe Bytes
renderMarkdown def =
    Nothing
```