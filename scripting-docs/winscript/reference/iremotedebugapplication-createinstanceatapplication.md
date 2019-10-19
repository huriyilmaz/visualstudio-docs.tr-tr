---
title: 'IRemoteDebugApplication:: Createınstanceatapplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.CreateInstanceAtApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CreateInstanceAtApplication
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285e5df6960e3188ffe1ce17b1fc4f43626a3d74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572314"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Uygulamanın işlem dışı olan koda göre uygulama işlemindeki nesnelerin oluşturulmasına izin verir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT CreateInstanceAtApplication(  
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
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IRemoteDebugApplication Arabirimi](../../winscript/reference/iremotedebugapplication-interface.md)