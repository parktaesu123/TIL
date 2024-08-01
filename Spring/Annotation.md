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

  # @Dynamicupdate

---

> Dirty checking으로 생성되는 update 쿼리 기본적으로 모든 필드를 업데이트한다.
> 
- JPA에서는 전체필드를 업데이트하는 방식을 기본값으로 사용한다.
- 전체필드를 업데이트 하는 방식의 장점
    - 생성되는 쿼리가 같아 **부트 실행시점에 미리 만들어서 재 사용** 가능합니다.
    - 데이터베이스 입장에서 쿼리 재 사용이 가능하다.
- 필드가 20개 이상일 경우에는 전체 필드 update가 부담스러울 수 있다.

### 이런 경우에 @Dynamicupdate를 사용하여 변경 필드만 반영되도록 한다.
