---
title: IMetaDataImport::ResolveTypeRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
ms.openlocfilehash: 800b15bb75e74898cee9d838900ea14b60620940
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431471"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef 方法
解析指定的 TypeRef 标记所表示的 <xref:System.Type> 引用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a>参数  
 `tr`  
 中要为其返回引用的类型信息的 TypeRef 元数据标记。  
  
 `riid`  
 中要在 `ppIScope`中返回的接口的 IID。 通常，这会 IID_IMetaDataImport。  
  
 `ppIScope`  
 弄用于定义所引用类型的模块范围的接口。  
  
 `ptd`  
 弄指向表示被引用类型的 TypeDef 标记的指针。  
  
## <a name="remarks"></a>备注  
  
> [!IMPORTANT]
> 如果加载多个应用程序域，请不要使用此方法。 方法不考虑应用程序域边界。 如果加载程序集的多个版本，并且这些版本包含相同命名空间的相同类型，则该方法将返回它找到的第一个类型的模块范围。  
  
 `ResolveTypeRef` 方法在其他模块中搜索类型定义。 如果找到类型定义，`ResolveTypeRef` 将返回该模块范围的接口，以及该类型的 TypeDef 标记。  
  
 如果要解析的类型引用的解析范围为 AssemblyRef，则 `ResolveTypeRef` 方法仅在已通过调用[IMetaDataDispenser：： OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法或[IMetaDataDispenser：： OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)方法打开的元数据范围内搜索匹配项。 这是因为 `ResolveTypeRef` 无法仅从磁盘或全局程序集缓存中存储程序集的 AssemblyRef 范围确定。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor  
  
 **库：** 作为资源包括在 Mscoree.dll 中  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [IMetaDataImport 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
