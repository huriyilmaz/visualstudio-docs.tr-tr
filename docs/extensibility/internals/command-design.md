---
title: Komut Tasarımı | Microsoft Docs
description: Visual Studio'da VSPackage için komut tasarlamayı Visual Studio. Dahil olmak üzere, nerede görüntülendiğinde, ne zaman kullanılabilir olduğunu ve nasıl iş olacağını belirtme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 48b438f457dea5aad5c241b0fd1e60daac3761a2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110572"
---
# <a name="command-design"></a>Komut tasarımı
VSPackage'a komut eklerken nerede görüntü olacağını, ne zaman kullanılabilir olduğunu ve nasıl işlen olacağını belirtmeniz gerekir.

## <a name="define-commands"></a>Komutları tanımlama
 Yeni komutlar tanımlamak için VSPackage Visual Studio bir komut tablosu (*.vsct*) dosyası dahil edildi. Visual Studio paket şablonunu kullanarak bir VSPackage oluşturduysanız, proje bu dosyalardan birini içerir. Daha fazla bilgi için [bkz. Visual Studio tablosu (.vsct) dosyaları.](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Visual Studio, bulduğu tüm *.vsct* dosyalarını birleştirarak komutları görüntüleyebiliyor. Bu dosyalar VSPackage ikili dosyalarından ayrı olduğundan, Visual Studio bulmak için paketi yüklemek zorunda değildir. Daha fazla bilgi için [bkz. VSPackage'lar kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Visual Studio menü kaynaklarını <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> ve komutlarını tanımlamak için kayıt özniteliğini kullanır. Daha fazla bilgi için [bkz. Komut uygulaması.](../../extensibility/internals/command-implementation.md)

 Komutlar çalışma zamanında birkaç farklı şekilde değiştirilebilir. Bunlar görüntülenebilir, gizlenir, etkinleştirilebilir veya devre dışı bırakılabilir. Farklı metin veya simgeler display veya farklı değerler içerebilirler. VSPackage'nızı yüklemeden önce Visual Studio özelleştirme gerçekleştirebilirsiniz. Daha fazla bilgi için [bkz. VSPackage'lar kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

## <a name="command-handlers"></a>Komut işleyicileri
 Bir komut oluşturdukta, komutu yürütmek için bir olay işleyicisi sağlayabilirsiniz. Kullanıcı komutu seçerse, uygun şekilde yönlendirildi olması gerekir. Komutu yönlendirme, komutu etkinleştirmek veya devre dışı bırakmak, gizlemek veya görüntülemek ve kullanıcı bunu seçerse yürütmek için doğru VSPackage'a göndermek anlamına gelir. Daha fazla bilgi için [bkz. Komut yönlendirme algoritması.](../../extensibility/internals/command-routing-algorithm.md)

## <a name="visual-studio-command-environment"></a>Visual Studio ortamını kullanın
 Visual Studio sayıda VSPackage barındırabilirsiniz ve her biri kendi komut kümesine katkıda bulunabilirsiniz. Ortam yalnızca geçerli göreve uygun komutları görüntüler. Daha fazla bilgi için [bkz. Komut kullanılabilirliği](../../extensibility/internals/command-availability.md) [ve Seçim bağlam nesneleri.](../../extensibility/internals/selection-context-objects.md)

 Yeni komutları, menüleri, araç çubuklarını veya kısayol menülerini tanımlayan VSPackage, yerel veya yönetilen derlemelerde kaynaklara başvurulan kayıt defteri girdileri aracılığıyla yükleme zamanında Visual Studio'ye komut bilgilerini sağlar. Her kaynak daha sonra bir ikili veri kaynağı (*.cto*) dosyasına başvurur ve bu dosya bir komut tablosu (*.vsct*) Visual Studio derlenin. Bu, Visual Studio vsPackage yüklemek zorunda kalmadan birleştirilmiş komut kümeleri, menüler ve araç çubukları sağlamalarını sağlar.

### <a name="command-organization"></a>Komut organizasyonu
 Ortam komutları gruba, önceliğe ve menüye göre konumlar.

- Gruplar, ilgili komutların mantıksal koleksiyonlarıdır; örneğin, **Kes,** **Kopyala** ve **Yapıştır komut** grubu. Gruplar, menülerde görünen komutlardır.

- Öncelik, bir gruptaki tek tek komutların menüde görünme sıralamalarını belirler.

- Menüler, gruplar için kapsayıcı olarak kullanılır.

  Ortam bazı komutları, grupları ve menüleri önceden tanımlar. Daha fazla bilgi için [bkz. Varsayılan komut, grup ve araç çubuğu yerleşimi.](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

  Bir komut birincil gruba atanabilir. Birincil grup, komutun ana menü yapısında ve Özelleştir iletişim kutusundaki **konumunu** kontrol eder. Bir komut birden çok grupta görünebilir; Örneğin, komut ana menüde, kısayol menüsünde ve araç çubuğunda olabilir. Daha fazla bilgi için [bkz. VSPackage'lar kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

### <a name="command-routing"></a>Komut yönlendirme
 VSPackage'lar için komutları çağırma ve yönlendirme işlemi, nesne örneklerde yöntemleri çağırma işleminden farklıdır.

 Ortam, komutları geçerli seçimi temel alan en içteki (yerel) komut bağlamından en dıştaki (genel) bağlama sırayla yönlendiriyor. Komutu yürüten ilk bağlam, komutu yürüten bağlamdır. Daha fazla bilgi için [bkz. Komut yönlendirme algoritması.](../../extensibility/internals/command-routing-algorithm.md)

 Çoğu örnekte ortam, komutları arabirimini kullanarak <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> işlemeye devam eder. Komut yönlendirme düzeni komutları işlemek için birçok farklı nesne olanaklı olduğundan, herhangi bir sayıda nesne tarafından uygulanamaz; bunlar Microsoft ActiveX denetimleri, pencere görünümü uygulamaları, belge nesneleri, proje hiyerarşileri ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> VSPackage nesnelerinin kendileridir (genel komutlar için). Bazı özel durumlarda, örneğin, bir hiyerarşide yönlendirme komutları, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> arabiriminin uygulanması gerekir.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Komut uygulaması](../../extensibility/internals/command-implementation.md)|VSPackage'da komutların nasıl uygulandığını açıklar.|
|[Komut kullanılabilirliği](../../extensibility/internals/command-availability.md)|Bu Visual Studio hangi komutların kullanılabilir olduğunu nasıl belirler?|
|[Komut yönlendirme algoritması](../../extensibility/internals/command-routing-algorithm.md)|Komut yönlendirme Visual Studio komutlarının farklı VSPackage'lar tarafından nasıl işlenene kadar olanaklı olduğunu açıklar.|
|[Komut yerleştirme yönergeleri](../../extensibility/internals/command-placement-guidelines.md)|Komutların ortam ortamında nasıl Visual Studio önerir.|
|[VSPackage'lar kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|VSPackages'ın komut mimarisini en iyi Visual Studio açıklar.|
|[Varsayılan komut, grup ve araç çubuğu yerleşimi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|VSPackage'ların Visual Studio'a dahil edilen komutları en iyi şekilde nasıl kullanabileceğini Visual Studio.|
|[VSPackage’ları Yönetme](../../extensibility/managing-vspackages.md)|VSPackage'Visual Studio yüklerini açıklar.|
|[Visual Studio tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|VSPackage'larda komutların düzenini ve görünümünü açıklamak için kullanılan XML tabanlı *.vsct* dosyaları hakkında bilgi sağlar.|
