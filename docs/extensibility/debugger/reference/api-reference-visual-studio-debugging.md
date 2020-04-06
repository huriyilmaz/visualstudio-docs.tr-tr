---
title: API Başvuru (Visual Studio Hata Ayıklama) | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738182"
---
# <a name="api-reference-visual-studio-debugging"></a>API Başvurusu (Visual Studio Hata Ayıklama)
Başvuru bölümü, API'nin kavramsal bir genel görünümünü, tüm API öğeleriiçin sözdizimini ve kullanımını gösteren bir kılavuz ve kod örneklerinin çeşitlisini içerir. Tüm başvurular kategoriye göre alfabetik olarak listelenir.

 Aşağıdaki tablo, yöntemlerle döndürülen ortak `HRESULT` değerleri gösterir.

|Adı|Açıklama|Değer|
|----------|-----------------|-----------|
|S_OK|Başarılı.|0x00000000|
|E_unexpected|Beklenmeyen hata.|0x8000FFFF|
|E_notımpl|Uygulanmaz.|0x80004001|
|E_outofmemory|İşlemi tamamlamak için yeterli bellek yok.|0x8007000E|
|E_ınvalıdarg|Bir veya daha fazla bağımsız değişken geçersizdir.|0x80070057|
|E_noınterface|Böyle bir arayüz desteklenmedi.|0x80004002|
|E_POINTER|Geçersiz işaretçi.|0x80004003|
|E_HANDLE|Geçersiz tutamak.|0x80070006|
|E_ABORT|Operasyon iptal edildi.|0x80004004|
|E_faıl|Beklenmeyen hata.|0x80004005|
|E_ACCESSDENIED|Genel erişim reddedildi hatası.|0x80070005|

> [!NOTE]
> Hata [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ayıklama yöntemi döndürdüğünde, `S_OK`tüm parametre işaretçileringeçerli olduğu varsayılır, yani döndürüldüğünde `S_OK` parametre işaretçileri üzerinde doğrulama yapılmaz.
>
> [!NOTE]
> Geçersiz veya `NULL` [out] parametreleri IDE'nin çökmesine neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Hata Ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Visual Studio Hata Ayıklayıcı Genişletilebilirliği](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
