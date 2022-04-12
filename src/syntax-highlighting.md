# Demo

**Syntax highlighting for Solidity**

  ```solidity
  // INSECURE
  mapping (address => uint) private userBalances;

  function transfer(address to, uint amount) {
      if (userBalances[msg.sender] >= amount) {
         userBalances[to] += amount;
         userBalances[msg.sender] -= amount;
      }
  }

  function withdrawBalance() public {
      uint amountToWithdraw = userBalances[msg.sender];
      // At the below point, the caller's code is executed, and can call transfer()
      (bool success, ) = msg.sender.call.value(amountToWithdraw)("");
      require(success);
      userBalances[msg.sender] = 0;
  }
  ```

**Syntax highlighting for LLVM IR**

  ```llvm
  ; ModuleID = 'logs/integer.bc'
  source_filename = "integer.c"
  target datalayout = "e-m:e-p270:32:32-p271:32:32-p272:64:64-i64:64-f80:128-n8:16:32:64-S128"
  target triple = "x86_64-unknown-linux-gnu"

  @r = dso_local global i32 1, align 4
  @s = dso_local global i32 2, align 4

  ; Function Attrs: noinline nounwind uwtable
  define dso_local i32 @main(i32 %0) #0 {
    %2 = alloca i32, align 4
    %3 = alloca i32, align 4
    %4 = alloca i32, align 4
    %5 = alloca i32, align 4
    %6 = alloca i32, align 4
    store i32 0, i32* %2, align 4
    store i32 %0, i32* %3, align 4
    store i32 1, i32* %4, align 4
    %7 = load i32, i32* %4, align 4
    %8 = load i32, i32* %3, align 4
    %9 = add nsw i32 %7, %8
    store i32 %9, i32* %5, align 4
    %10 = load i32, i32* %5, align 4
    %11 = icmp sgt i32 %10, 1
    br i1 %11, label %12, label %13

  12:                                               ; preds = %1
    store i32 2, i32* %5, align 4
    br label %18

  13:                                               ; preds = %1
    %14 = load i32, i32* %5, align 4
    store i32 %14, i32* %6, align 4
    %15 = load i32, i32* %6, align 4
    %16 = load i32, i32* %3, align 4
    %17 = add nsw i32 %15, %16
    store i32 %17, i32* %5, align 4
    store i32 3, i32* %5, align 4
    br label %18

  18:                                               ; preds = %13, %12
    %19 = load i32, i32* @s, align 4
    %20 = load i32, i32* %4, align 4
    %21 = add nsw i32 %19, %20
    store i32 %21, i32* @r, align 4
    %22 = load i32, i32* @r, align 4
    ret i32 %22
  }

  attributes #0 = { noinline nounwind uwtable "frame-pointer"="all" "min-legal-vector-width"="0" "no-trapping-math"="true" "stack-protector-buffer-size"="8" "target-cpu"="x86-64" "target-features"="+cx8,+fxsr,+mmx,+sse,+sse2,+x87" "tune-cpu"="generic" }

  !llvm.module.flags = !{!0, !1, !2}
  !llvm.ident = !{!3}

  !0 = !{i32 1, !"wchar_size", i32 4}
  !1 = !{i32 7, !"uwtable", i32 1}
  !2 = !{i32 7, !"frame-pointer", i32 2}
  !3 = !{!"clang version 13.0.1 (git@github.com:sbip-sg/llvm-project f2884905c5582465c71cdeabd6905b1f9df27346)"}
  ```
