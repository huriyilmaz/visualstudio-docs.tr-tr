---
title: Komutlar, menüler ve araç çubukları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: 61
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 337bc4de9171d2f98bf0be0068b298b7f600b979
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155844"
---
# <a name="commands-menus-and-toolbars"></a>Komutlar, Menüler ve Araç Çubukları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Menüler ve araç çubukları, kullanıcıların VSPackage içindeki komutlara erişme yöntemidir. Komutlar, bir belge yazdırmak, bir görünümü yenilemek veya yeni bir dosya oluşturmak gibi görevleri gerçekleştiren işlevlerdir. Menüler ve araç çubukları, komutlarınızı kullanıcılara sunmak için kullanışlı grafiksel yollardır. Genellikle, ilgili komutlar aynı menü ya da araç çubuğunda birlikte kümelenir.  
  
- Menüler genellikle tümleşik geliştirme ortamı (IDE) veya araç penceresinin en üstündeki bir satırda kümelenmiş tek sözcüklü dizeler olarak görüntülenir. Menüler, sağ tıklama olayının sonucu olarak da görüntülenebilir ve bu bağlamda kısayol menüleri olarak adlandırılır. Tıklandığında, menüler bir veya daha fazla komut görüntüleyecek şekilde genişler. Tıklandığı komutlar, görev gerçekleştirebilir veya ek komutlar içeren alt menüleri başlatabilir. Bazı iyi bilinen menü adları dosya, düzenleme, görüntüleme ve pencere. Daha fazla bilgi için bkz. [genişletme menüleri ve komutları](../../extensibility/extending-menus-and-commands.md).  
  
- Araç çubukları genellikle düğme satırları ve Birleşik giriş kutuları, liste kutuları, metin kutuları ve menü denetleyicileri gibi diğer denetimlerdir. Tüm araç çubuğu denetimleri komutlarla ilişkilendirilir. Bir araç çubuğu düğmesine tıkladığınızda, ilişkili komutu etkinleştirilir. Araç çubuğu düğmeleri genellikle Yazdır komutu için bir yazıcı gibi temel komutları öneren simgelere sahiptir. Açılan liste denetiminde, listedeki her öğe farklı bir komutla ilişkilendirilir. Bir menü denetleyicisi, denetimin bir tarafındaki bir araç çubuğu düğmesi ve diğer kenar, tıklandığında ek komutları görüntüleyen aşağı bir oktur. Daha fazla bilgi için bkz. [bir araç çubuğuna menü denetleyicisi ekleme](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
- Bir komut oluşturduğunuzda, bunun için de bir olay işleyicisi oluşturmanız gerekir. Olay işleyicisi, komutun görünür veya etkin olduğunu belirler, metnini değiştirmenize olanak sağlar ve etkinleştirildiğinde komutun uygun şekilde ("rotalar") yanıt vermesini sağlar. Çoğu örnekte IDE, arabirimi kullanarak komutları işler <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . Genel seçime bağlı olarak, en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] içteki komut bağlamından başlayarak, yerel seçime göre ve en dıştaki içeriğe devam eden bir hiyerarşik şekilde rotadaki komutlar. Ana menüye eklenen komutlar, komut dosyası oluşturma için hemen kullanılabilir. Daha fazla bilgi için bkz. [Menuıcommands vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) ve [seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md).  
  
  Yeni menüleri ve araç çubuklarını tanımlamak için bunları bir Visual Studio komut tablosu (. vsct) dosyasında açıklamanız gerekir. Visual Studio paket şablonu, bu dosyayı sizin için oluşturur ve şablonda seçtiğiniz komutları, araç çubuklarını ve düzenleyicileri desteklemek için gerekli öğeleri sağlar. Alternatif olarak, burada açıklanan XML şemasını kullanarak kendi. vsct dosyanızı yazabilirsiniz: [VSCT XML şema başvurusu](../../extensibility/vsct-xml-schema-reference.md).  
  
  . Vsct dosyaları ile çalışma hakkında daha fazla bilgi için bkz. [Visual Studio komut tablosu (. Vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
  Bu bölümdeki konularda, komut, menü ve araç çubuklarının VSPackages 'te nasıl çalıştığı açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Komut tablosu biçim belirtiminin derinlemesine bir açıklaması.  
  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Komut tabloları için XML tabanlı sözdizimi ve derleyicisini açıklar.  
  
 [Varsayılan Komut, Grup ve Araç Çubuğu Yerleşimi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Önceden tanımlanmış komutlar, gruplar, menüler ve araç çubuklarını açıklar.  
  
 [IDE Tanımlı Komutlar, Menüler ve Gruplar](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 IDE tarafından kullanılabilecek önceden tanımlanmış menüleri, komutları ve komut gruplarını belirtir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Komut Tasarımı](../../extensibility/internals/command-design.md)  
 Komutların nasıl tasarlanacağını açıklar.  
  
 [Menü ve Araç Çubuğu Komutlarını En İyi Duruma Getirme](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Komutlar için yönergeler sağlar.  
  
 [Komutları Kullanılabilir Yapma](../../extensibility/internals/making-commands-available.md)  
 Komutların Visual Studio için nasıl kullanılabilir yapılacağını açıklar.  
  
 [Birlikte Çalışma Bütünleştirilmiş Kodları Kullanan Komutlar ve Menüler](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Birlikte çalışma derlemelerini kullanan komutların nasıl uygulanacağını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [VSPackage’larda Komut Yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)  
 VSPackages 'de komut yönlendirmeyi açıklar.
