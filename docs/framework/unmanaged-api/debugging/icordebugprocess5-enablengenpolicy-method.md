---
title: ICorDebugProcess5::EnableNGENPolicy 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
ms.openlocfilehash: 9497bea9b7cc5eb98876c923858dbcbc6adf9d07
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792452"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>ICorDebugProcess5::EnableNGENPolicy 方法
设置一个值，该值确定应用程序在托管调试器下运行时如何加载本机映像。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a>参数  
 `ePolicy`  
 中确定应用程序在托管调试器下运行时如何加载本机映像的[CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md)常量。  
  
## <a name="remarks"></a>备注  
 如果策略设置成功，则该方法将返回 `S_OK`。 如果 `ePolicy` 超出[CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md)定义的枚举值的范围，则该方法将返回 `E_INVALIDARG` 并且方法调用不起作用。 如果无法更新本机映像生成器（Ngen.exe）的策略，该方法将返回 `E_FAIL`。  
  
 在进程的生存期内，可以随时调用 `ICorDebugProcess5::EnableNGenPolicy` 方法。 此策略对设置策略后加载的任何模块有效。  
  
## <a name="requirements"></a>需求  
 **平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [ICorDebugProcess5 接口](icordebugprocess5-interface.md)
- [调试接口](debugging-interfaces.md)
- [调试](index.md)
