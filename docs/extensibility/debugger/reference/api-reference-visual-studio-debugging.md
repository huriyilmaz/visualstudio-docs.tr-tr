---
description: Başvuru bölümünde API'ye kavramsal bir genel bakış, tüm API öğeleri için söz dizimi ve kullanımı gösteren bir kılavuz ve çeşitli kod örnekleri yer almaktadır.
title: API Başvurusu (Visual Studio Ayıklama) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ac51ded5f99fc2d73d09e563bdf05ee0ac40469f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073207"
---
# <a name="api-reference-visual-studio-debugging"></a>API Başvurusu (Visual Studio Hata Ayıklama)
Başvuru bölümünde API'ye kavramsal bir genel bakış, tüm API öğeleri için söz dizimi ve kullanımı gösteren bir kılavuz ve çeşitli kod örnekleri yer almaktadır. Tüm başvurular kategoriye göre alfabetik olarak listelenir.

 Aşağıdaki tablo, yöntemler tarafından `HRESULT` döndürülen ortak değerleri gösterir.

|Ad|Açıklama|Değer|
|----------|-----------------|-----------|
|S_OK|Başarılı.|0x00000000|
|E_unexpected|Beklenmeyen hata.|0x8000FFFF|
|E_notımpl|Uygulanmaz.|0x80004001|
|E_outofmemory|işlemi tamamlamak için yeterli bellek yok.|0x8007000E|
|E_ınvalıdarg|Bir veya daha fazla bağımsız değişken geçersiz.|0x80070057|
|E_noınterface|Böyle bir arabirim desteklenmiyor.|0x80004002|
|E_POINTER|Geçersiz işaretçi.|0x80004003|
|E_HANDLE|Geçersiz tanıtıcı.|0x80070006|
|E_ABORT|İşlem durduruldu.|0x80004004|
|E_faıl|Beklenmeyen hata.|0x80004005|
|E_ACCESSDENIED|Genel erişim reddedildi hatası.|0x80070005|

> [!NOTE]
> Bir hata ayıklama yöntemi döndür olduğunda, tüm out parametre işaretçilerinin geçerli olduğu varsayılır; başka bir şekilde, döndürülen parametre işaretçileri üzerinde [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] `S_OK` doğrulama `S_OK` yürütülmz.
>
> [!NOTE]
> Geçersiz `NULL` veya [out] parametreleri IDE'nin kilitlenmesi neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Hata Ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Visual Studio Hata Ayıklayıcı Genişletilebilirliği](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
