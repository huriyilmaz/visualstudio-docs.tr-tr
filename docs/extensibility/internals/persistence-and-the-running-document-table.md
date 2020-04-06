---
title: Kalıcılık ve Çalışan Belge Tablosu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba698f20b83d1a7af42aeca046aa2a8c943838ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706715"
---
# <a name="persistence-and-the-running-document-table"></a>Kalıcılık ve Çalıştırılan Belge Tablosu
IDE'de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeler, hizmeti kullanarak gerçekleştirdikleri proje öğelerinin kalıcılığını yönetmekten <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>tamamen sorumludur. Belgeler Visual Studio ortamında ki temel kalıcılık birimidir. Projeler, tüm açık belgelerin durumunu izleyen bir kaynak olan çalışan belge tablosu (RDT) ile belgelerin açılmasını, kaydedilmesini ve yeniden adlandırılacağını koordine emz.

## <a name="managing-persistence"></a>Kalıcılığı Yönetme
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> Projeler, arabirimi uygulayarak ortamın kalıcılık hizmetini denetler. Ortam hiçbir zaman bir belgeden kendisini kalıcı olarak devam etmesini asla istemese de, sahibi olan projeden (veya hiyerarşiden) belgeyi kaydetmesini ister. Bu, projenin proje öğesi verilerini yerel dosyalara, uzak dosyalara, veritabanına, depoya veya başka bir ortama kaydetmesini mümkün kılar.

 Küresel ortam RDT'yi korur. Ortam, RDT'deki tüm açık pencereler ve belgeler için girişleri tutar ve bu da çözümün kapatılması gibi özel bildirimler almalarını mümkün kılar. Buna ek olarak, RDT, ortamın **Çözüm Gezgini'nde**karşılık gelen düğümlerini izlemesini mümkün kılar. RDT, hem proje dosyaları hem de proje öğesi belgeleri de dahil olmak üzere açık ve kalıcı nesne başına bir kayıt tutar.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalıştırılan Belge Tablosu](../../extensibility/internals/running-document-table.md)
- [IDE’de Seçim ve Para Birimi](../../extensibility/internals/selection-and-currency-in-the-ide.md)
