# Покрытие кода тестами #

## Процент покрытия тестами ## 

сигнатура

    import "testing"
    func TestFuncname(t *testing.T){

    }

просто тест\
`go test -v`
>-v - дополнительная информация по тестам


выводит в кончоль процент покрытия \
`go test -v -cover`  

создает файл отчет о анализе покрытия \
`go test -coverprofile  cover.out`

создает html отчет о покрытии кода \
`go tool cover -html  cover.out -o cover.html`

----
## Бенчмарк ##

 сигнатура тестовой функции

    import "testing"
    func BenchmarkFuncname(b *testing.B){ 
        for i:=0;i< b.N; i++{
            
         }
    }

команда \
`go test -bench . -benchmem ./unpack_test.go`

----
## pprof ##

`go test -bench . -benchmem -cpuprofile cpu.out -memprofile mem.out -memprofilerate=1 namefile.go namefile_test.go`

далее выбрать файл для анализа 

`go tool pprof cpu.out` \
либо \
`go tool pprof mem.out`

далее выбрать функцию 

`(pprof) list name_function`

Графическое изображение анализа 

> возможно понадобиться установить Graphviz \
> [сайт]:https://graphviz.org/download/

`go tool pprof -http=localhost:8080 mem.out`