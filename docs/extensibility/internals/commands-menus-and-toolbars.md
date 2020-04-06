---
title: Komutlar, Menüler ve Araç Çubukları | Microsoft Dokümanlar
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
ms.openlocfilehash: 2be2f719d0f123328d5c518c08e30df2185e2a19
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709496"
---
# <a name="commands-menus-and-toolbars"></a>Komutlar, menüler ve araç çubukları
Menüler ve araç çubukları, kullanıcıların VSPackage'ınızdaki komutlara erişme şeklidir. Komutlar, belge yazdırma, görünümü yenileme veya yeni bir dosya oluşturma gibi görevleri gerçekleştiren işlevlerdir. Menüler ve araç çubukları, komutlarınızı kullanıcılara sunmanın kullanışlı grafik yollarıdır. Genellikle, ilgili komutlar aynı menü veya araç çubuğunda birlikte kümelenir.

- Menüler genellikle tümleşik geliştirme ortamının (IDE) veya bir araç penceresinin üst kısmında bir satırda kümelenmiş tek sözcükdizelleri olarak görüntülenir. Menüler, sağ tıklatma olayının sonucu olarak da görüntülenebilir ve bu bağlamda kısayol menüleri olarak adlandırılır. Tıklatıldığında, menüler bir veya daha fazla komutgörüntülemek için genişletilir. Komutlar, tıklatıldığında görevleri gerçekleştirebilir veya ek komutlar içeren alt menüler başlatabilir. Bazı iyi bilinen menü adları **Dosya**, **Edit**, **Görünüm**ve **Pencere**vardır. Daha fazla bilgi için [menüleri ve komutları genişlet'e](../../extensibility/extending-menus-and-commands.md)bakın.

- Araç çubukları genellikle açılan kutular, liste kutuları, metin kutuları ve menü denetleyicileri gibi düğme satırları ve diğer denetimlerdir. Tüm araç çubuğu denetimleri komutlarla ilişkilidir. Bir araç çubuğu düğmesini tıklattığınızda, ilişkili komutu etkinleştirilir. Araç çubuğu düğmelerinde genellikle Yazdırma komutu için yazıcı gibi temel komutları öneren simgeler vardır. Açılan liste denetiminde, listedeki her öğe farklı bir komutla ilişkilidir. Menü denetleyicisi, denetimin bir tarafının araç çubuğu düğmesi, diğer tarafının ise tıklatıldığında ek komutlar görüntüleyen bir aşağı ok olduğu bir melezdir. Daha fazla bilgi için [bkz.](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)

- Bir komut oluşturduğunuzda, bunun için bir olay işleyicisi de oluşturmanız gerekir. Olay işleyicisi komutun ne zaman görünür veya etkin olduğunu belirler, metnini değiştirmenize olanak tanır ve etkinleştirildiğinde komutun uygun şekilde yanıt vermesine ("rotalar") olanak tanır. Çoğu durumda, IDE <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi kullanarak komutları işler. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Yerel seçilim temel alınarak en içteki komut bağlamından başlayarak hiyerarşik bir şekilde rotadaki komutlar ve genel seçime dayalı olarak en dıştaki içeriğe doğru ilerler. Ana menüye eklenen komutlar komut dosyası için hemen kullanılabilir. Daha fazla bilgi için [MenuCommands vs. OleMenuKomutları](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015) ve [Seçim bağlamı nesnelerine](../../extensibility/internals/selection-context-objects.md)bakın.

  Yeni menüler ve araç çubukları tanımlamak için bunları Visual Studio komut tablosunda (*.vsct*) dosyasında açıklamanız gerekir. Visual Studio paket şablonu, şablonda seçtiğiniz komutları, araç çubuklarını ve editörleri desteklemek için gerekli öğelerle birlikte bu dosyayı sizin için oluşturur. Alternatif olarak, burada açıklanan XML şema kullanarak kendi *.vsct* dosyanızı yazabilirsiniz: [VSCT XML şema referans.](../../extensibility/vsct-xml-schema-reference.md)

  .vsct dosyalarıyla çalışma hakkında daha fazla bilgi için [Visual Studio komut tablosu (.vsct) dosyalarına](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)bakın. *.vsct*

  Bu bölümdeki konular, komutların, menülerin ve araç çubuklarının VSPackages'te nasıl çalıştığını açıklar.

## <a name="in-this-section"></a>Bu bölümde
- [VSPackages kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Komut tablosu biçimi belirtiminin ayrıntılı bir açıklaması.

- [Visual Studio komut tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Komut tabloları için XML tabanlı sözdizimini ve derleyiciyi açıklar.

- [Varsayılan komut, grup ve araç çubuğu yerleşimi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 Önceden tanımlanmış komutları, grupları, menüleri ve araç çubuklarını açıklar.

- [IDE tanımlı komutlar, menüler ve gruplar](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE tarafından kullanılmak üzere önceden tanımlanmış menüleri, komutları ve komut gruplarını belirtir.

- [Komut tasarımı](../../extensibility/internals/command-design.md)

 Komutların nasıl tasarlanılabildiğini açıklar.

- [Menü ve araç çubuğu komutlarını optimize edin](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 Komutlar için yönergeler verir.

- [Komutları kullanılabilir hale getirin](../../extensibility/internals/making-commands-available.md)

 Visual Studio'da komutların nasıl kullanılabilir hale getirilebildiğini açıklar.

- [Interop derlemeleri kullanan komutlar ve menüler](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Interop derlemeleri kullanan komutların nasıl uygulanacağını açıklar.

## <a name="related-sections"></a>İlgili bölümler
- [VSPackages komut yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)

 VSPackages'te komut yönlendirmeyi açıklar.
