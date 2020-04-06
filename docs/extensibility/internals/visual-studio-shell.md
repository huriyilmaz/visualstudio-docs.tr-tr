---
title: Görsel Stüdyo Kabuk | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb89fc3b82dc7f142714608d8a669e368216c729
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704000"
---
# <a name="visual-studio-shell"></a>Visual Studio Kabuğu
Kabuk, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]''nin' içinde tümleştirmenin birincil aracısIdur. Kabuk, VSPackages'in ortak hizmetleri paylaşmasını sağlamak için gerekli işlevselliği sağlar. Mimari amacı VSPackages birincil işlevselliği yelek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] olduğundan, kabuk temel işlevsellik sağlamak ve bileşeni VSPackages arasında çapraz iletişimi desteklemek için bir çerçevedir.

## <a name="shell-responsibilities"></a>Kabuk Sorumlulukları
 Kabuğun aşağıdaki temel sorumlulukları vardır:

- Kullanıcı arabiriminin (UI) temel öğelerini (COM arabirimleri aracılığıyla) destekleme. Bunlar varsayılan menüler ve araç çubukları, belge pencere çerçeveleri veya çok belgearabirimi (MDI) alt pencereleri ve araç penceresi çerçeveleri ve yerleştirme desteği içerir.

- Belgelerin kalıcılığını koordine etmek ve bir belgenin birden fazla şekilde açılamayacağını veya uyumsuz bir şekilde açılamayacağını garanti etmek için çalışan belge tablosunda (RDT) çalışan tüm belgelerin çalışan bir listesini tutmak.

- Komut yönlendirme ve komut işleme arabirimini `IOleCommandTarget`destekleyen, .

- VSPackages'ı uygun zamanlarda yükleme. Bir VSPackage'ın gecikmeli yüklenmesi, kabuğun performansını artırmak için gereklidir.

- Temel kabuk işlevselliği <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>sağlayan ve <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>temel pencereleme işlevselliği sağlayan belirli paylaşılan hizmetleri yönetme.

- Çözüm (.sln) dosyalarını yönetme. Çözümler, Visual C++ 6.0'daki çalışma alanı (.dsw) dosyalarına benzer ilişkili proje grupları içerir.

- Kabuk genelinde seçim, bağlam ve para birimini izleme. Kabuk aşağıdaki öğe türlerini izler:

  - Geçerli proje

  - Geçerli proje öğesi veya ItemID geçerli<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - **Özellikler** penceresi için geçerli seçim veya`SelectionContainer`

  - Komutların, menülerin ve araç çubuklarının görünürlüğünü kontrol eden UI bağlam ı veya CmdUIGuids

  - Etkin pencere, belge ve geri al yöneticisi gibi şu anda etkin olan öğeler

  - Dinamik Yardım'ı yönlendiren Kullanıcı Bağlamı öznitelikleri

  Kabuk ayrıca yüklü VSPackages ve mevcut hizmetler arasında iletişim aracılık. Kabuğun temel özelliklerini destekler ve tüm VSPackages entegre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]için kullanılabilir hale getirir. Bu temel özellikler aşağıdaki öğeleri içerir:

- İletişim kutusu ve sıçrama ekranı **hakkında**

- **Yeni Ekle ve Varolan Öğe** iletişim kutusu ekle

- **Sınıf Görünüm** penceresi ve **Nesne Tarayıcısı**

- **Başvurular** iletişim kutusu

- **Belge Anahat** penceresi

- **Dinamik Yardım** penceresi

- **Bul** ve **Değiştir**

- **Yeni** menüde Proje ve **Dosya Aç** iletişim kutularını **aç**

- **Araçlar** menüsündeki **Seçenekler** iletişim kutusu

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
