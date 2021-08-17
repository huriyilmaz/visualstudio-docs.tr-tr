---
title: Kalıcılık ve çalışan belge tablosu | Microsoft Docs
description: projenin Visual Studio ıde 'deki belge durumunu izleyen, çalışan belge tablosunda belge açma, kaydetme ve yeniden adlandırmayı nasıl koordine edin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ec0c2e9018625b733e8f5c5c6f9270bd9b28cab1eadb54a026562d798b54ec74
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401511"
---
# <a name="persistence-and-the-running-document-table"></a>Kalıcılık ve Çalıştırılan Belge Tablosu
IDE 'de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projeler, hizmet kullanarak gerçekleştirdikleri proje öğelerinin kalıcılığını yönetmekten tamamen sorumludur <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . belgeler Visual Studio ortamındaki temel kalıcılık birimidir. Projeler, tüm açık belgelerin durumunu izleyen bir kaynak olan çalışan belge tablosu (RDT) ile belgeleri açma, kaydetme ve yeniden adlandırmayı koordine.

## <a name="managing-persistence"></a>Kalıcılığı yönetme
 Projeler, arabirimi uygulayarak ortamın Kalıcılık hizmetini denetler <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> . Ortam hiçbir şekilde doğrudan bir belge kalıcı hale getirirken, belgeyi kaydetmek için sahip olan projeye (veya hiyerarşiye) sorulur. Bu, projenin proje öğesi verilerini yerel dosyalara, uzak dosyalara, bir veritabanına, depoya veya diğer bir ortama kaydetmesini olanaklı kılar.

 Genel ortam, RDT 'yi korur. Ortam, bir çözümün kapatıldığı zaman gibi özel bildirimler almasına olanak sağlayan RDT 'deki tüm açık pencereler ve belgeler için girişleri tutar. Ayrıca, RDT, ortamın **Çözüm Gezgini** içinde karşılık gelen düğümlerini izlemesini mümkün hale getirir. RDT, her iki proje dosyası ve proje-öğe belgeleri de dahil olmak üzere açık ve kalıcı bir nesne başına bir kayıt tutar.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalıştırılan Belge Tablosu](../../extensibility/internals/running-document-table.md)
- [IDE’de Seçim ve Para Birimi](../../extensibility/internals/selection-and-currency-in-the-ide.md)
