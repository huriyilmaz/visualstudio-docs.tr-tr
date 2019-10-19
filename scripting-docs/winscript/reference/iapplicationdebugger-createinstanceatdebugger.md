---
title: 'Iapplicationdebugger:: Createınstanceatdebugger | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.CreateInstanceAtDebugger
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c15dc5d9b36a718ed41813bac46bc4b9415eb853
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577885"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Hata ayıklayıcı için işlem dışı olan kod tarafından hata ayıklayıcı işleminde nesne oluşturulmasına izin verir.  
  
> [!IMPORTANT]
> Güvenilmeyen kodun güvenilir bir hata ayıklayıcı iş parçacığında rastgele nesneler oluşturmasına izin verdiği için bu yöntem uygulanmamalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT CreateInstanceAtDebugger(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `rclsid`  
 'ndaki Oluşturulacak nesnenin sınıf tanımlayıcısı (CLSID).  
  
 `pUnkOuter`  
 'ndaki @No__t_0, nesne bir toplamanın parçası olarak oluşturulmaz. Aksi takdirde, `pUnkOuter` toplama nesnesinin `IUnknown` arabirimine yönelik bir işaretçidir (denetim `IUnknown`).  
  
 `dwClsContext`  
 'ndaki Çalıştırılabilir kodu çalıştırmak için bağlam. Değerler `CLSCTX` numaralandırmasından alınır.  
  
 `riid`  
 'ndaki Nesneyle iletişim kurmak için kullanılan arabirim tanımlayıcısı.  
  
 `ppvObject`  
 dışı @No__t_0 istenen arabirim işaretçisini alan işaretçi değişkeninin adresi. Başarılı döndürmeden sonra, istenen arabirim işaretçisini içeren * `ppvObject`. Hata sonrasında, \* `ppvObject` `NULL` içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem `CoCreateInstance` devreder.  
  
 Yöntem şu anda uygulanmadı.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IApplicationDebugger Arabirimi](../../winscript/reference/iapplicationdebugger-interface.md)