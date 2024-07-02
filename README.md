# Shīkensu

> シーケンス
> Sequence

Run a sequence of functions on in-memory representations of files.
__Build static websites with ease__, without conforming to a specific structure.

### Markdown example

```gren
import Bytes exposing ( Bytes )
import FileSystem.Path as Path exposing ( Path )
import Shikensu
import Shikensu.Contrib as Shikensu
import Shikensu.Definition as Shikensu
import Task


main : Shikensu.Program
main =
    -- 🚀 List current directory
    Shikensu.program sequence Path.empty


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


destination : Path
destination =
    Path.fromPosix "./dist"


renderMarkdown : Shikensu.Definition -> Maybe Bytes
renderMarkdown def =
    Maybe.map renderMarkdownBytes def.content
```
