---
title: Visual Studio Kabuğu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60aa48da701857508f9b6fd7fc3d9d0c0603046e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722050"
---
# <a name="visual-studio-shell"></a>Visual Studio Kabuğu
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kabuğu, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]tümleştirmenin birincil aracısıdır. Kabuk, VSPackages 'ın ortak hizmetleri paylaşmasını sağlamak için gerekli işlevleri sağlar. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 'ın mimari amacı VSPackages 'te birincil işlevselliğe Vest çünkü kabuk, temel işlevleri sağlamak ve kendi bileşeni VSPackages 'ler arasında çapraz iletişimi desteklemek için bir çerçevedir.

## <a name="shell-responsibilities"></a>Kabuk sorumlulukları
 Kabukta aşağıdaki önemli sorumluluklar vardır:

- Destekleyici (COM arabirimleri aracılığıyla) Kullanıcı arabiriminin temel öğeleri (UI). Bunlar arasında varsayılan menüler ve araç çubukları, belge penceresi çerçeveleri veya çok belgeli arabirim (MDI) alt pencereleri ve araç penceresi çerçeveleri ve yerleştirme desteği bulunur.

- Belgelerin kalıcılığını koordine etmek ve bir belgenin birden fazla yoldan veya uyumsuz yollarla açılabileceğinden emin olmak için, çalışan bir belge tablosunda (RDT) Şu anda açık olan tüm belgelerin çalışmakta olan bir listesini koruyun.

- Komut yönlendirme ve komut işleme arabirimini destekleme, `IOleCommandTarget`.

- VSPackages, uygun zamanlarda yükleniyor. Kabuğun performansını iyileştirmek için VSPackage gecikme yükleme gerekir.

- Temel bir kabuk işlevselliği sağlayan <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>gibi bazı paylaşılan hizmetleri yönetme ve temel Pencereleme işlevselliği sağlayan <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>.

- Çözüm (. sln) dosyalarını yönetme. Çözümler, Visual C++ 6,0 çalışma alanı (. DSW) dosyalarına benzer şekilde ilgili proje gruplarını içerir.

- Kabuk genelinde seçimi, bağlamı ve para birimini izleme. Kabuk aşağıdaki öğe türlerini izler:

  - Geçerli proje

  - Geçerli proje öğesi veya öğe kimliği geçerli <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - **Özellikler** penceresi veya `SelectionContainer` için geçerli seçim

  - Komutların, menülerin ve araç çubuklarının görünürlüğünü denetleyen UI bağlam kimlikleri veya Cmduiguid 'Leri

  - Etkin pencere, belge ve geri alma yöneticisi gibi şu anda etkin olan öğeler

  - Dinamik yardım 'ı hedefleyen Kullanıcı bağlamı öznitelikleri

  Kabuk Ayrıca yüklü VSPackages ve geçerli hizmetler arasındaki iletişimi de dengeler. Bu, kabuğun temel özelliklerini destekler ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]tümleştirilmiş tüm VSPackages tarafından kullanılabilir hale getirir. Bu temel özellikler aşağıdaki öğeleri içerir:

- İletişim kutusu ve giriş ekranı **hakkında**

- **Yeni ve varolan öğe** Ekle iletişim kutuları

- **Sınıf görünümü** pencere ve **nesne tarayıcısı**

- **Başvurular** iletişim kutusu

- **Belge Anahattı** penceresi

- **Dinamik yardım** penceresi

- **Bul** ve **Değiştir**

- **Yeni** menüde **Proje Aç** ve **Dosya Aç** iletişim kutuları

- **Araçlar** menüsündeki **Seçenekler** iletişim kutusu

- **Özellikler** penceresi

- **Çözüm Gezgini**

- **Görev listesi** penceresi

- **Araç Kutusu**

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackage’lar](../../extensibility/internals/vspackages.md)