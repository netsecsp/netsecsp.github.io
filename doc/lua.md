# lua 插件  

基于lua-5.4.4实现IOsCommand接口，用于打通asynframe framework，支持IOsCommand/IVmHost接口  

## 导出函数  
```c++  
HRESULT __stdcall CreateCommand( /*[in ]*/InstancesManager *lpInstancesManager, /*[in ]*/IUnknown **ppParam1, /*[in ]*/uint64_t param2, /*[out]*/IOsCommand **ppObject)  
```  

## 开发  
创建lua对象
```c++  
spCommand.Attach(asynsdk::CreateCommand(lpInstancesManager, "lua", 0, 0, 0));
if( spCommand )
{
    spCommand->Execute(0, STRING_from_string("open"), &STRING_from_string("test.lua"), 1, 0); //执行test.lua脚本
    spCommand->Execute(0, STRING_from_string("exec"), &STRING_from_string("print("This is my world!")"), 1, 0); //执行lua脚本块
}
```  

## 例子  
\support\testlua\testapi  