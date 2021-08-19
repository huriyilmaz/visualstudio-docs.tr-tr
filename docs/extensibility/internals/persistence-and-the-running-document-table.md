---
title: Kalıcılık ve Çalışan Belge Tablosu | Microsoft Docs
description: Projelerin, IDE'de belge durumunu takip edecek şekilde çalışan belge tablosunda belge açma, kaydetme ve yeniden Visual Studio öğrenin.
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
ms.openlocfilehash: 1c4b37e5ae834a614cb741cb7589dad9dd1d6677
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063128"
---
# <a name="persistence-and-the-running-document-table"></a>Kalıcılık ve Çalıştırılan Belge Tablosu
IDE'de projeler, proje öğelerinin kalıcılığı yönetiminden tamamen sorumludur ve bu da hizmetini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> gerçekleştirmektedir. Belgeler, belge ortamındaki temel kalıcılık Visual Studio birimidir. Projeler, açık olan tüm belgelerin durumunu takip edecek bir kaynak olan çalışan belge tablosu (RDT) ile belgelerin açılmasını, kaydedi ve yeniden yeniden anını koordine ediyor.

## <a name="managing-persistence"></a>Kalıcılığı Yönetme
 Projeler, arabirimini kullanarak ortamın kalıcılık hizmetini <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> kontrol eder. Ortam hiçbir zaman doğrudan bir belgeden kendi kendine kalıcılık isterken, sahibi olan projeden (veya hiyerarşiden) belgeyi kaydetmesini ister. Bu, projenin proje öğesi verilerini yerel dosyalara, uzak dosyalara, veritabanına, depoya veya başka bir ortama kaydetmesini mümkün yapar.

 Genel ortam RDT'yi sürdürür. Ortam, RDT'de tüm açık pencereler ve belgeler için girdileri bulundurarak çözüm kapatılanlar gibi özel bildirimler almalarını mümkün kılmıştır. Ayrıca RDT, ortamın içinde karşılık gelen düğümlerini izlemesini mümkün **Çözüm Gezgini.** RDT, hem proje dosyaları hem de proje öğesi belgeleri de dahil olmak üzere açık, kalıcı nesne başına bir kayıt bulundurabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalıştırılan Belge Tablosu](../../extensibility/internals/running-document-table.md)
- [IDE’de Seçim ve Para Birimi](../../extensibility/internals/selection-and-currency-in-the-ide.md)
