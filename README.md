# Shīkensu

> シーケンス    
> Sequence

Run a sequence of functions on in-memory representations of files.  
__Build static websites with ease__, without conforming to a specific structure.

### Markdown example

```gren
module Main exposing ( main )

import Bytes exposing ( Bytes )
import Bytes.Decode as Bytes
import FileSystem
import Shikensu
import Shikensu.Contrib as Shikensu
import Shikensu.Definition as Shikensu
import Shikensu.Focus as Shikensu exposing ( Focus(..) )
import Shikensu.Path as Path
import Task


main : Shikensu.Program
main =
    Shikensu.program sequence


sequence : FileSystem.Permission -> Shikensu.Task
sequence fsPermission =
    [ ".."
    , "example"
    , "content"
    ]
        |> Path.directory
        |> Relative
        |> Shikensu.list fsPermission
        |> Task.map (Shikensu.withExtension "md")
        |> Task.andThen (Shikensu.read fsPermission)
        |> Task.map
                (\compendium ->
                    compendium
                        |> Shikensu.permalink "index"
                        |> Shikensu.renameExtension "md" "html"
                        |> Shikensu.renderContent renderMarkdown
                )
        |> Task.andThen (Shikensu.write fsPermission buildDir)


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
    Maybe.map Bytes.decode (Debug.log "" def.content)
```