---
title: İç içe projeler için Sihirbaz Desteği | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7f37700d908167ebef8c071021558822bdce173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703201"
---
# <a name="wizard-support-for-nested-projects"></a>İç içe Projeler için Sihirbaz Desteği
IDE iç içe projeler için ana proje uygulayabilirsiniz iki sihirbazları çalışır: **Yeni Proje** sihirbazı ve **Öğe Ekle** sihirbazı.

 Bir kullanıcı **Yeni Proje** sihirbazını Dosya menüsünde **Yeni Proje** **Ekle'yi** seçerek veya Çözüm Gezgini'nde Yeni **Proje** **Ekle'yi** seçerek veya sağ tıklayarak Başlatıyorsa, IDE **AddProject** komutunu çalıştırıyor ve üst projenin **AddProject** komutunu çalıştırıyor veya bir dizi bağlam parametresi olan bir sihirbaz (.vsz) dosyasını döndürür.

 Benzer şekilde, bir üst projenin **AddItem** sihirbazları uygulaması, farklı bağlam parametreleri kümesine sahip bir .vsz dosyayı döndürür.

 Sihirbazlar hakkında daha fazla bilgi için [bkz. Vsz) Dosya](../../extensibility/internals/wizard-dot-vsz-file.md), [Bağlam Parametreleri](../../extensibility/internals/context-parameters.md) ve [Kayıt Proje ve Madde Şablonları](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Projeleri İç İçe Geçirme](../../extensibility/internals/nesting-projects.md)
