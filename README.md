# UnitTest
單元測試練習專案

**1. [建立專案產生被測試類別]** 

主控台應用程式 (.NET Core)] 專案範本

專案命名為 Bank

被測試類別為BankAccount.cs

在 [ 建置 ] 功能表上按一下 [ 建置方案]

**2. [建立單元測試專案]**

MSTest 測試專案 (.NET Core)] 專案範本

專案命名為 BankTests

BankTests 專案就會新增至 Bank 方案中

在 BankTests 專案中新增 Bank 專案的參考

在 [方案總管] 中選取 BankTests 專案下方的 [相依性] 然後從右鍵功能表選擇 [新增參考]

在 [參考管理員] 對話方塊中展開 [專案] 並選取 [方案] 然後選取 [Bank] 項目

**3. [建立測試類別]**

測試類別為BankAccount.cs 類別中有三種方法

**Debit_WithValidAmount_UpdatesBalance 用來測試Debit方法產出結果是否如預期**

AreEqual 方法用來確認結果如預期

把BankAccount.cs檔案中的Debit方法m_balance -= amount改成 m_balance += amount 

在測試總管中 執行測式則會產生錯誤

**Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange 用來測試Debit方法傳入參數是否小於零或者大於設定參數**

ThrowsException 方法來判斷擲回正確的例外狀況  除非擲回 ArgumentOutOfRangeException 否則此方法會造成測試失敗


**Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange**

**沒有辦法知道哪些條件 (amount > m_balance 或 amount < 0) 會導致測試期間擲回例外狀況**

 **進一步改善要測試的方法**
 
 用TRY CATCH捕抓失敗訊息
 StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage) 來比對Debit方法產生的失敗訊息是不是我們要的
 
 最後因為要確認測試式有效的有失敗訊息回來 加上 return及Assert.Fail("The expected exception was not thrown.");
 
