> @PathVariable
> 
- URL에 변수를 넣어주는 어노테이션
1. @GetMapping이나 @PostMapping 같은 매핑해주는 어노테이션의 URL부분에 상용될 변수명을 입력한다.
2. @PathVariable 안에 URL부분에 입력한 변수명을 동일하게 추가한다.

```java
@GetMapping("/board/modify/{id}")
    public String boardModify(@PathVariable("id") Integer id,
                              Model model){
        model.addAttribute("board", boardService.boardView(id));

        return "boardmodify";
    }
    
     @PostMapping("/board/update/{id}")
    public String boardUpdate(@PathVariable("id") Integer id,
    Board board)
    {
        //기존 글
        Board boardTemp = boardService.boardView(id);
        //새 글
        boardTemp.setTitle(board.getTitle());
        boardTemp.setContent(board.getContent());
        boardService.write(boardTemp);

        return "redirect:/board/list";
    }
```
