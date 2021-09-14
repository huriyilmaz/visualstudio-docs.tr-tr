---
title: Komutlar, Menüler ve Araç Çubukları | Microsoft Docs
description: VsPackage'larda ne olduğu ve nasıl Visual Studio komutlar, menüler ve araç çubukları hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a38bee13afb83afed022dc69f046f87ec64f7adb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636217"
---
# <a name="commands-menus-and-toolbars"></a>Komutlar, menüler ve araç çubukları
Menüler ve araç çubukları, kullanıcıların VSPackage'lı komutlara erişme yolu olur. Komutlar, bir belge yazdırma, görünümü yenileme veya yeni dosya oluşturma gibi görevleri gerçekleştiren işlevlerdir. Menüler ve araç çubukları, komutlarınızı kullanıcılara sunmak için kullanışlı grafik yollardır. Genellikle, ilgili komutlar aynı menü veya araç çubuğunda birlikte kümelenmiş olur.

- Menüler genellikle tümleşik geliştirme ortamının (IDE) veya araç penceresinin üst kısmında bir satırda kümelenmiş tek sözcük dizeler olarak görüntülenir. Menüler ayrıca sağ tıklama olayı sonucu olarak da görüntülenebilir ve bu bağlamda kısayol menüleri olarak adlandırılır. Tıklarken, menüler bir veya daha fazla komut görüntüleyecek şekilde genişler. Komutlar, tıklarken ek komutlar içeren görevleri gerçekleştirebilir veya alt menüleri başlatabilirsiniz. Bazı iyi bilinen menü adları **Dosya,** **Düzenle,** Görüntüle **ve** **Pencere'dir.** Daha fazla bilgi için bkz. [Menüleri ve komutları genişletme.](../../extensibility/extending-menus-and-commands.md)

- Araç çubukları genellikle düğmelerin ve birleşik giriş kutuları, liste kutuları, metin kutuları ve menü denetleyicileri gibi diğer denetimlerin satırlarıdır. Tüm araç çubuğu denetimleri komutlarla ilişkilendirildi. Bir araç çubuğu düğmesine tıklarsanız, ilişkili komutu etkinleştirilir. Araç çubuğu düğmeleri genellikle yazdırma komutu için yazıcı gibi temel komutları öneren simgeler içerir. Açılan liste denetiminde, listede yer alan her öğe farklı bir komutla ilişkilendirilr. Menü denetleyicisi, denetimin bir tarafının bir araç çubuğu düğmesi, diğerinin ise tıkıldığında ek komutları görüntüleyen aşağı ok olduğu karmadır. Daha fazla bilgi için [bkz. Araç çubuğuna menü denetleyicisi ekleme.](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)

- Bir komut oluşturdukta bunun için bir olay işleyicisi de oluşturmanız gerekir. Olay işleyicisi komutun ne zaman görünür veya etkin olduğunu belirler, metnini değiştirmenize olanak sağlar ve etkinleştirildiğinde komutun uygun şekilde yanıt vermesini ("yollar") sağlar. Çoğu örnekte IDE, komutları arabirimini kullanarak <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> işlemeye devam ediyor. Yerel seçimi temel alarak en içteki komut bağlamıyla başlayarak hiyerarşik bir şekilde yönlendirilen komutlar ve genel seçime göre en dıştaki bağlama [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] devam eder. Ana menüye eklenen komutlar betikler için hemen kullanılabilir. Daha fazla bilgi için bkz. [MenuCommands ve OleMenuCommands ve](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015) [Seçim bağlam nesneleri.](../../extensibility/internals/selection-context-objects.md)

  Yeni menüleri ve araç çubuklarını tanımlamak için bunları bir komut Visual Studio (*.vsct*) dosyasında açıklamanız gerekir. Bu Visual Studio şablonu, şablonda seçtiğiniz komutları, araç çubuklarını ve düzenleyicileri desteklemek için gerekli öğelerle birlikte bu dosyayı sizin için oluşturur. Alternatif olarak, burada açıklanan XML şemasını kullanarak kendi *.vsct* dosyanızı [yazabilirsiniz: VSCT XML şema başvurusu.](../../extensibility/vsct-xml-schema-reference.md)

  *.vsct* dosyalarıyla çalışma hakkında daha fazla bilgi için [bkz. Visual Studio tablosu (.vsct) dosyaları.](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

  Bu bölümdeki konu başlıkları vsPackage'larda komutların, menülerin ve araç çubuklarının nasıl çalışa bir şekilde çalışa olduğunu açıklar.

## <a name="in-this-section"></a>Bu bölümde
- [VSPackage'lar kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Komut tablosu biçimi belirtimlerinin ayrıntılı açıklaması.

- [Visual Studio tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Komut tabloları için XML tabanlı söz dizimi ve derleyiciyi açıklar.

- [Varsayılan komut, grup ve araç çubuğu yerleşimi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 Önceden tanımlanmış komutları, grupları, menüleri ve araç çubuklarını açıklar.

- [IDE tanımlı komutlar, menüler ve gruplar](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 IDE tarafından kullanılabilen önceden tanımlanmış menüleri, komutları ve komut gruplarını [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] belirtir.

- [Komut tasarımı](../../extensibility/internals/command-design.md)

 Komutların nasıl tasarımını açıklar.

- [Menü ve araç çubuğu komutlarını iyileştirme](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 Komutlar için yönergeler sağlar.

- [Komutları kullanılabilir yapma](../../extensibility/internals/making-commands-available.md)

 Komutlar için kullanılabilir hale Visual Studio.

- [Birlikte çalışma derlemeleri kullanan komutlar ve menüler](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Birlikte çalışma derlemeleri kullanan komutların nasıl uygulandığını açıklar.

## <a name="related-sections"></a>İlgili bölümler
- [VSPackage'larda komut yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)

 VSPackage'larda komut yönlendirmeyi açıklar.