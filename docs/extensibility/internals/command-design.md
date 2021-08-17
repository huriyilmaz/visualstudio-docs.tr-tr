---
title: Komut tasarımı | Microsoft Docs
description: Visual Studio bir VSPackage için komut tasarlama hakkında bilgi edinin. Dahil olmak üzere nerede göründüğünü, ne zaman kullanılabileceğini ve nasıl işleneceğini belirtme.
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
ms.openlocfilehash: c02049819487df474898c2c40319ed4a6d13db294ed5d34da84743c0eb4b50a1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376267"
---
# <a name="command-design"></a>Komut tasarımı
VSPackage 'a bir komut eklediğinizde, nerede görüneceğini, kullanılabilir olduğunda ve nasıl işleneceğini belirtmeniz gerekir.

## <a name="define-commands"></a>Komutları tanımlama
 yeni komutlar tanımlamak için vspackage projenize bir Visual Studio komut tablosu (*. vsct*) dosyası ekleyin. Visual Studio paket şablonunu kullanarak bir vspackage oluşturduysanız, proje bu dosyalardan birini içerir. daha fazla bilgi için bkz. [Visual Studio komut tablosu (. vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

 Visual Studio komutları görüntülemesi için bulduğu tüm *. vsct* dosyalarını birleştirir. bu dosyalar vspackage ikilisinden farklı olduğundan, Visual Studio komutları bulmak için paketi yüklemek zorunda değildir. Daha fazla bilgi için bkz. [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Visual Studio, <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> menü kaynaklarını ve komutları tanımlamak için kayıt özniteliğini kullanır. Daha fazla bilgi için bkz. [komut uygulama](../../extensibility/internals/command-implementation.md).

 Komutlar, çalışma zamanında çeşitli yollarla değiştirilebilir. Bunlar görüntülenebilir veya gizli, etkinleştirilebilir veya devre dışı bırakılabilir. Farklı metin veya simgeleri görüntüleyebilir veya farklı değerler içerebilir. Visual Studio vspackage 'ı yüklemeden önce harika bir özelleştirme gerçekleştirilebilir. Daha fazla bilgi için bkz. [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

## <a name="command-handlers"></a>Komut işleyicileri
 Bir komut oluşturduğunuzda, komutunu yürütmek için bir olay işleyicisi sağlamanız gerekir. Kullanıcı komutu seçerse, uygun şekilde yönlendirilmelidir. Komut yönlendirmesi, bunu etkinleştirmek veya devre dışı bırakmak, onu gizlemek veya göstermek ve Kullanıcı bunu seçerse yürütmek için doğru VSPackage 'a gönderilmesi anlamına gelir. Daha fazla bilgi için bkz. [komut yönlendirme algoritması](../../extensibility/internals/command-routing-algorithm.md).

## <a name="visual-studio-command-environment"></a>Visual Studio komut ortamı
 Visual Studio herhangi bir sayıda vspackages barındırabilir ve her biri kendi komut kümesini katkıda bulunabilir. Ortam yalnızca geçerli göreve uygun olan komutları görüntüler. Daha fazla bilgi için bkz. [komut kullanılabilirliği](../../extensibility/internals/command-availability.md) ve [seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md).

 yeni komutlar, menüler, araç çubukları veya kısayol menülerini tanımlayan bir vspackage, yerel veya yönetilen derlemelerdeki kaynaklara başvuran kayıt defteri girişleri aracılığıyla, yükleme sırasında Visual Studio komut bilgilerini sağlar. her kaynak daha sonra bir Visual Studio komut tablosu (*. vsct*) dosyası derlerken üretilen bir ikili veri kaynağı (*. cto*) dosyasına başvurur. bu, Visual Studio her yüklü vspackage yüklemesine gerek duymadan birleştirilmiş komut kümeleri, menüler ve araç çubukları sağlamanıza olanak sağlar.

### <a name="command-organization"></a>Komut organizasyonu
 Ortam komutları gruba, önceliğe ve menüye göre konumlandırır.

- Gruplar, ilgili komutların mantıksal koleksiyonlarıdır, örneğin **Kes**, **Kopyala** ve **Yapıştır** komut grubu. Gruplar menülerde görüntülenen komutlardır.

- Öncelik, bir gruptaki bireysel komutların menüde görünme sırasını belirler.

- Menüler, gruplar için kapsayıcı olarak davranır.

  Ortam, bazı komutları, grupları ve menüleri önceden tanımlar. Daha fazla bilgi için bkz. [varsayılan komut, Grup ve araç çubuğu yerleşimi](../../extensibility/internals/default-command-group-and-toolbar-placement.md).

  Bir komut, birincil gruba atanabilir. Birincil grup, komutun konumunu ana menü yapısında ve **Özelleştir** iletişim kutusunda denetler. Bir komut, birden çok grupta görünebilir; Örneğin, bir komut ana menüde, kısayol menüsünde ve bir araç çubuğunda olabilir. Daha fazla bilgi için bkz. [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

### <a name="command-routing"></a>Komut yönlendirme
 VSPackages için çağırma ve Yönlendirme komutları nesne örneklerine çağırma sürecinden farklıdır.

 Ortam komutları, geçerli seçime dayalı olan en dıştaki (yerel) komut bağlamından ardışık olarak (genel) içeriğine yönlendirir. Komutu yürütebilecek ilk bağlam onu işleyen bir. Daha fazla bilgi için bkz. [komut yönlendirme algoritması](../../extensibility/internals/command-routing-algorithm.md).

 Çoğu örnekte, ortam komutları arabirimini kullanarak işler <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . komut yönlendirme şeması birçok farklı nesnenin komutları işlemesini sağladığından, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> herhangi bir sayıda nesne tarafından uygulanabilir. bunlar Microsoft ActiveX denetimlerini, pencere görünümü uygulamalarını, belge nesnelerini, proje hiyerarşilerini ve vspackage nesnelerini (genel komutlar için) içerir. Bazı özel durumlarda (örneğin, bir hiyerarşideki yönlendirme komutları), <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> arabirimin uygulanması gerekir.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Komut uygulama](../../extensibility/internals/command-implementation.md)|Bir VSPackage içinde komutların nasıl uygulanacağını açıklar.|
|[Komut kullanılabilirliği](../../extensibility/internals/command-availability.md)|Visual Studio bağlamın hangi komutların kullanılabilir olduğunu nasıl belirlediğini açıklar.|
|[Komut yönlendirme algoritması](../../extensibility/internals/command-routing-algorithm.md)|komut yönlendirme mimarisinin Visual Studio, komutların farklı vspackages tarafından nasıl işleneceğini açıklar.|
|[Komut yerleştirme yönergeleri](../../extensibility/internals/command-placement-guidelines.md)|Visual Studio ortamında komutların nasıl konumlandıralınacağını önerir.|
|[VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|vspackages 'ın Visual Studio komut mimarisine en iyi şekilde nasıl yararlanılacağını açıklar.|
|[Varsayılan komut, Grup ve araç çubuğu yerleşimi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|VSPackages 'ın Visual Studio eklenen komutları en iyi şekilde nasıl kullandığını açıklar.|
|[VSPackage’ları Yönetme](../../extensibility/managing-vspackages.md)|Visual Studio vspackages 'ın nasıl yükleneceğini açıklar.|
|[komut tablosu (. vsct) dosyaları Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|VSPackages içindeki komutların yerleşimini ve görünümünü anlatmak için kullanılan XML tabanlı *. vsct* dosyaları hakkında bilgi sağlar.|
