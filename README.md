# Nordhold-Cheat-Hack-Infinite-Honor-(V1.1.1)
Get yourself some honor point with Cheat Engine (Nordhold V1.1.1)

1. Install Cheat Engine
2. Open Nordhold.
3. Open Cheat Engine, Click the First Icon at left-side and choose NordHold.exe.
4. Click "Memory View" and CTRL+G , go to address GameAssembly.dll+6ED330
5. CTRL+A , then paste the code below and click "execute/run". (if you want less honor please change the value in code as i have no idea how to revert back the changes)
6. Try to change your honor value in the honor skill tree (assign/revert skill) and your honor should changed to whatever value you set.


//----Code Start Here----

[ENABLE]

alloc(newmem, 2048, "GameAssembly.dll")

label(return)

newmem:

  // R8D is the 'amount' parameter in x64
  
  mov r8d, #999999   
  
  // Original code we replaced
  
  mov [rsp+08],rbx
  
  jmp return

"GameAssembly.dll"+6ED330:

  jmp newmem
  
return:

[DISABLE]

"GameAssembly.dll"+6ED330:

  // Restore the original instruction
  
  mov [rsp+08],rbx
  
dealloc(newmem)

// ----Code Ends Here---- <br><br>

// Tool used to find the address: https://il2cppdumper.com/
