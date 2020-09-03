---
title: API başvurusu (Visual Studio hata ayıklama) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a2df6d82099a927664620e19096107f283afada
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738182"
---
# <a name="api-reference-visual-studio-debugging"></a>API Başvurusu (Visual Studio Hata Ayıklama)
Başvuru bölümü, API 'ye kavramsal genel bakış, tüm API öğelerinin sözdizimini ve kullanımını gösteren bir kılavuz ve kod örnekleri örneği içerir. Tüm başvurular kategoriye göre alfabetik olarak listelenir.

 Aşağıdaki tabloda `HRESULT` Yöntemler tarafından döndürülen ortak değerler gösterilmektedir.

|Ad|Açıklama|Değer|
|----------|-----------------|-----------|
|S_OK|Başarılı.|0x00000000|
|E_UNEXPECTED|Beklenmeyen hata.|0x8000FFFF|
|E_NOTIMPL|Uygulanmaz.|0x80004001|
|E_OUTOFMEMORY|İşlemi tamamlamaya yetecek bellek yok.|0x8007000E|
|E_INVALIDARG|Bir veya daha fazla bağımsız değişken geçersiz.|0x80070057|
|E_NOINTERFACE|Böyle bir arabirim desteklenmiyordur.|0x80004002|
|E_POINTER|Geçersiz işaretçi.|0x80004003|
|E_HANDLE|Geçersiz tanıtıcı.|0x80070006|
|E_ABORT|İşlem iptal edildi.|0x80004004|
|E_FAIL|Beklenmeyen hata.|0x80004005|
|E_ACCESSDENIED|Genel erişim reddedildi hatası.|0x80070005|

> [!NOTE]
> Bir [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] hata ayıklama yöntemi `S_OK` döndürüldüğünde, tüm out parametre işaretçilerinin geçerli olduğu varsayılır, yani, döndürülen parametre işaretçileri üzerinde hiçbir doğrulama yapılmaz `S_OK` .
>
> [!NOTE]
> Geçersiz veya `NULL` [out] PARAMETRELERI IDE 'nin kilitlenmesine neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Hata Ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Visual Studio Hata Ayıklayıcı Genişletilebilirliği](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
