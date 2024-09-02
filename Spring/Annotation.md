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
---
> @id , @generatedValue
> 
- JPA로 테이블과 엔티티를 매핑할 때 식별자로 사용할 필드위에  @id를 붙여서 테이블의 PK와 매핑시켜준다.
- 위와같이 PK를 매핑시켜주면 새로운 행(튜플)이 생성될 때마다 수동적으로 식별자를 넣어줘야 된다는 불편을 해결해주는 것이 @generatedValue이다.
- @generatedValue는 새로운 행이 생성될 때 자동으로 식별자(PK)를 넣어준다.
---
> @Column
> 
- 객체의 필드를 테이블의 칼럼에 매핑 시켜주는 어노테이션
