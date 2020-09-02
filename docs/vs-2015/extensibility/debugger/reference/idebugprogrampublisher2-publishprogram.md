---
title: IDebugProgramPublisher2::P ublishProgram | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 21bc6e558eff662874ac35eb8557f01838914ca9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547344"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem, bir programı hata ayıklama motorları (DEs) ve oturum hata ayıklama Yöneticisi için kullanılabilir hale getirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   LPCOLESTR        szFriendlyName,  
   IUnknown*        pDebuggeeInterface  
);  
```  
  
```csharp  
int PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   string           szFriendlyName,  
   object           pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Engines`  
 'ndaki Bu programı başlatabileceği veya bu programa ekleyebileceğiniz DEs için GUID dizisi.  
  
 `szFriendlyName`  
 'ndaki Program için kolay ad (Bu, kullanıcıya sunulan menülerde veya iletişim kutularında görünür).  
  
 `pDebuggeeInterface`  
 [in] `IUnknown` program arabirimi (Bu değer programı benzersiz bir şekilde tanımlamak için bir tanımlama bilgisi olarak kullanılır; Bu aynı değer programı "yayımdan kaldırmak" için kullanılır)  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir programı artık hata ayıklama için kullanılamaz hale getirmek için, [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)' ı çağırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)
