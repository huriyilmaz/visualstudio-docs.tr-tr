---
title: Komutlar, menüler ve araç çubukları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65f5a43bee5a89492bc1ecc7bf7c1126b5a80456
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173596"
---
# <a name="commands-menus-and-toolbars"></a>Komutlar, menüler ve araç çubukları
Menüler ve araç çubukları, kullanıcıların VSPackage içindeki komutlara erişme yöntemidir. Komutlar, bir belge yazdırmak, bir görünümü yenilemek veya yeni bir dosya oluşturmak gibi görevleri gerçekleştiren işlevlerdir. Menüler ve araç çubukları, komutlarınızı kullanıcılara sunmak için kullanışlı grafiksel yollardır. Genellikle, ilgili komutlar aynı menü ya da araç çubuğunda birlikte kümelenir.

- Menüler genellikle tümleşik geliştirme ortamı (IDE) veya araç penceresinin en üstündeki bir satırda kümelenmiş tek sözcüklü dizeler olarak görüntülenir. Menüler, sağ tıklama olayının sonucu olarak da görüntülenebilir ve bu bağlamda kısayol menüleri olarak adlandırılır. Tıklandığında, menüler bir veya daha fazla komut görüntüleyecek şekilde genişler. Tıklandığı komutlar, görev gerçekleştirebilir veya ek komutlar içeren alt menüleri başlatabilir. Bazı iyi bilinen menü adları **Dosya**, **düzenleme**, **görüntüleme**ve **pencere**. Daha fazla bilgi için bkz. [menüleri ve komutları genişletme](../../extensibility/extending-menus-and-commands.md).

- Araç çubukları genellikle düğme satırları ve Birleşik giriş kutuları, liste kutuları, metin kutuları ve menü denetleyicileri gibi diğer denetimlerdir. Tüm araç çubuğu denetimleri komutlarla ilişkilendirilir. Bir araç çubuğu düğmesine tıkladığınızda, ilişkili komutu etkinleştirilir. Araç çubuğu düğmeleri genellikle Yazdır komutu için bir yazıcı gibi temel komutları öneren simgelere sahiptir. Açılan liste denetiminde, listedeki her öğe farklı bir komutla ilişkilendirilir. Bir menü denetleyicisi, denetimin bir tarafındaki bir araç çubuğu düğmesi ve diğer kenar, tıklandığında ek komutları görüntüleyen aşağı bir oktur. Daha fazla bilgi için bkz. [bir araç çubuğuna menü denetleyicisi ekleme](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).

- Bir komut oluşturduğunuzda, bunun için de bir olay işleyicisi oluşturmanız gerekir. Olay işleyicisi, komutun görünür veya etkin olduğunu belirler, metnini değiştirmenize olanak sağlar ve etkinleştirildiğinde komutun uygun şekilde ("rotalar") yanıt vermesini sağlar. Çoğu örnekte IDE, arabirimi kullanarak komutları işler <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . Genel seçime bağlı olarak, en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] içteki komut bağlamından başlayarak, yerel seçime göre ve en dıştaki içeriğe devam eden bir hiyerarşik şekilde rotadaki komutlar. Ana menüye eklenen komutlar, komut dosyası oluşturma için hemen kullanılabilir. Daha fazla bilgi için bkz. [menuıcommands vs. OleMenuCommands](/visualstudio/misc/menucommands-vs-olemenucommands?view=vs-2015) ve [seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md).

  Yeni menüleri ve araç çubuklarını tanımlamak için bunları bir Visual Studio komut tablosu (*. vsct*) dosyasında açıklamanız gerekir. Visual Studio paket şablonu, bu dosyayı sizin için oluşturur ve şablonda seçtiğiniz komutları, araç çubuklarını ve düzenleyicileri desteklemek için gerekli öğeleri sağlar. Alternatif olarak, burada açıklanan XML şemasını kullanarak kendi *. vsct* dosyanızı yazabilirsiniz: [VSCT XML şema başvurusu](../../extensibility/vsct-xml-schema-reference.md).

  *. Vsct* dosyaları ile çalışma hakkında daha fazla bilgi için bkz. [Visual Studio komut tablosu (. vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

  Bu bölümdeki konularda, komut, menü ve araç çubuklarının VSPackages 'te nasıl çalıştığı açıklanmaktadır.

## <a name="in-this-section"></a>Bu bölümde
- [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Komut tablosu biçim belirtiminin derinlemesine bir açıklaması.

- [Visual Studio komut tablosu (. vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Komut tabloları için XML tabanlı sözdizimi ve derleyicisini açıklar.

- [Varsayılan komut, Grup ve araç çubuğu yerleşimi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 Önceden tanımlanmış komutlar, gruplar, menüler ve araç çubuklarını açıklar.

- [IDE tanımlı komutlar, menüler ve gruplar](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 IDE tarafından kullanılabilecek önceden tanımlanmış menüleri, komutları ve komut gruplarını belirtir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Komut tasarımı](../../extensibility/internals/command-design.md)

 Komutların nasıl tasarlanacağını açıklar.

- [Menüyü ve araç çubuğu komutlarını iyileştirme](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 Komutlar için yönergeler sağlar.

- [Komutları kullanılabilir yap](../../extensibility/internals/making-commands-available.md)

 Komutların Visual Studio için nasıl kullanılabilir yapılacağını açıklar.

- [Birlikte çalışma derlemelerini kullanan komutlar ve menüler](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Birlikte çalışma derlemelerini kullanan komutların nasıl uygulanacağını açıklar.

## <a name="related-sections"></a>İlgili bölümler
- [VSPackages 'de komut yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)

 VSPackages 'de komut yönlendirmeyi açıklar.
