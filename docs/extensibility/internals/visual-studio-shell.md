---
title: Visual Studio Kabuk | Microsoft Docs
description: Visual Studio kabuğu, Visual Studio tümleştirmenin birincil aracısıdır ve temel işlevsellik sağlar ve VSPackage'lar arasında çapraz iletişimi destekler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7f57defce4eb9b46185f0d266822b5f4a0d2e719
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117650"
---
# <a name="visual-studio-shell"></a>Visual Studio Kabuğu
Kabuk, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] içinde tümleştirmenin birincil aracısıdır. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kabuk, VSPackage'ların ortak hizmetleri paylaşması için gerekli işlevselliği sağlar. 'nin mimari hedefi VSPackage'larda birincil işlevselliği en iyi şekilde kullanmak olduğundan kabuk, temel işlevler sağlayan ve bileşeni VSPackage'ları arasında çapraz iletişimi destekleyen bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çerçevedir.

## <a name="shell-responsibilities"></a>Kabuk Sorumlulukları
 Kabuğun aşağıdaki temel sorumlulukları vardır:

- Kullanıcı arabiriminin (UI) temel öğelerini destekleme (COM arabirimleri aracılığıyla). Bunlar varsayılan menüler ve araç çubukları, belge penceresi çerçeveleri veya çok belgeli arabirim (MDI) alt pencereleri ile araç penceresi çerçeveleri ve yerleştirme desteğidir.

- Belgelerin kalıcılığıyla eşgüdüm sağlamak ve bir belgenin birden fazla şekilde veya uyumsuz yollarla açılamaysini garanti etmek için, çalışan bir belge tablosunda (RDT) açık olan tüm belgelerin çalışan listesinin korunması.

- Komut yönlendirme ve komut işleme arabirimini destekleme, `IOleCommandTarget` .

- VSPackage'ları uygun zamanlarda yükleme. Kabuğun performansını geliştirmek için VSPackage'ın gecikmeli yüklenmesi gerekir.

- Temel kabuk işlevselliği sağlayan ve temel pencere işlevselliği sağlayan gibi bazı paylaşılan <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> hizmetleri yönetme.

- Çözüm (.sln) dosyalarını yönetme. Çözümler, 6.0'daki çalışma alanı (.dsw) dosyalarına benzer Visual C++ grupları içerir.

- Kabuk genelinde seçimi, bağlamı ve para birimini izleme. Kabuk aşağıdaki öğe türlerini izler:

  - Geçerli proje

  - Geçerli proje öğesi veya geçerli ÖğeKimlik Numarası <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - Özellikler penceresi için **geçerli seçim** veya `SelectionContainer`

  - Komutların, menülerin ve araç çubuklarının görünürlüğünü kontrol altına alan kullanıcı arabirimi bağlam kimlikleri veya CmdUIGuids

  - Etkin pencere, belge ve geri alma yöneticisi gibi şu anda etkin olan öğeler

  - Dinamik Yardım'a yol alan Kullanıcı Bağlamı öznitelikleri

  Kabuk ayrıca yüklü VSPackage'lar ve geçerli hizmetler arasındaki iletişime de aracılık sağlar. Kabuğun temel özelliklerini destekler ve ile tümleştirilmiş tüm VSPackage'lar tarafından [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanılabilir. Bu temel özellikler aşağıdaki öğeleri içerir:

- **İletişim** kutusu ve giriş ekranı hakkında

- **Yeni Ekle ve Var Olan Öğeyi Ekle iletişim** kutuları

- **Sınıf Görünümü** penceresi ve **Nesne Tarayıcısı**

- **Başvurular** iletişim kutusu

- **Belge Ana Hat** penceresi

- **Dinamik Yardım** penceresi

- **Bul** ve **Değiştir**

- **Yeni Project** aç **ve** Dosya Aç iletişim **kutuları**

- **Araçlar** menüsündeki Seçenekler **iletişim** kutusu

- **Özellikler** penceresi

- **Çözüm Gezgini**

- **Görev Listesi** penceresi

- **Araç Kutusu**

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackage’lar](../../extensibility/internals/vspackages.md)
