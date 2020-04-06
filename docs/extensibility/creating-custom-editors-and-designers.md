---
title: Özel Editörler ve Tasarımcılar Oluşturma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9f56b82225e1e40782b6753bea03d3c1780f596
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739481"
---
# <a name="create-custom-editors-and-designers"></a>Özel editörler ve tasarımcılar oluşturun

Visual Studio entegre geliştirme ortamı (IDE) farklı editör türlerini barındırabilir:

- Visual Studio çekirdek editörü

- Özel editörler

- Dış Editörler

- Tasarımcılar

Aşağıdaki bilgiler, gereksinim duyduğunuz düzenleyici türünü seçmenize yardımcı olur.

## <a name="types-of-editor"></a>Editör türleri

Visual Studio çekirdek editörü hakkında daha fazla bilgi için [editör ve dil hizmetlerini genişlet'e](../extensibility/extending-the-editor-and-language-services.md)bakın.

### <a name="custom-editors"></a>Özel editörler
 Özel bir editör özel durumlarda çalışmak üzere tasarlanmış biridir. Örneğin, işlevi Microsoft Exchange sunucusu gibi belirli bir depoya veri okuyup yazmak olan bir düzenleyici oluşturabilirsiniz. Yalnızca proje türünüzle çalışan bir düzenleyici veya yalnızca birkaç özel komutu olan bir düzenleyici istiyorsanız özel bir düzenleyici seçin. Ancak, kullanıcıların standart [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeleri yeniden dizinetmek için özel bir düzenleyici kullanamayacağını unutmayın.

 Özel bir düzenleyici, bir düzenleyici fabrikasını kullanabilir ve kayıt defterine editör hakkında bilgi ekleyebilir. Ancak, özel düzenleyiciile ilişkili proje türü, özel düzenleyiciyi başka şekillerde anında atabilir.

 Özel bir düzenleyici, görünümü uygulamak için yerinde etkinleştirme veya basitleştirilmiş katıştırma kullanabilir.

### <a name="external-editors"></a>Dış editörler
 Dış editörler, Visual Studio'ya Microsoft Word, Not Defteri veya Microsoft FrontPage gibi tümleşik olmayan düzenleyicilerdir. Örneğin, VSPackage'ınızdan metin geçiriyorsanız, böyle bir düzenleyici yi çağırabilirsiniz. Dış editörler kendilerini kaydeder ve Visual Studio dışında kullanılabilir. Harici bir düzenleyiciyi çağırdığınızda ve ana bilgisayar penceresine katıştırılmış olabilir, sonra IDE'deki bir pencerede görünür. Değilse, IDE bunun için ayrı bir pencere oluşturur.

 Yöntem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> numaralandırmayı kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> belge önceliğini ayarlar. Değer `DP_External` belirtilirse, dosya harici bir düzenleyici tarafından açılabilir.

## <a name="editor-design-decisions"></a>Editör tasarım kararları
 Aşağıdaki tasarım soruları, uygulamanız için en uygun düzenleyici türünü seçmenize yardımcı olacaktır:

- Uygulamanız verilerini dosyalara kaydedecek mi, kaydetmez mi? Verilerini dosyalara kaydedecekse, özel veya standart biçimde mi olacak?

   Standart bir dosya biçimi kullanıyorsanız, projenize ek olarak diğer proje türleri onlara veri açıp okuyabilecek/yazabilecektir. Ancak, özel bir dosya biçimi kullanıyorsanız, yalnızca proje türünüz onlara veri açıp okuyabilir/yazabilir.

   Projeniz dosyaları kullanıyorsa, standart düzenleyiciyi özelleştirmeniz gerekir. Projeniz dosyaları kullanmıyorsa, ancak daha çok bir veritabanıveya başka bir depodaki öğeleri kullanıyorsa, özel bir düzenleyici oluşturmanız gerekir.

- Düzenleyicinizin ActiveX denetimlerini barındırması gerekiyor mu?

   Düzenleyiciniz ActiveX denetimlerini barındırıyorsa, [yerinde etkinleştirmede](/visualstudio/misc/in-place-activation?view=vs-2015)belirtildiği gibi yerinde etkinleştirme düzenleyicisi uygulayın. ActiveX denetimlerini barındırmıyorsa, basitleştirilmiş bir katıştırma düzenleyicisi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kullanın veya varsayılan düzenleyiciyi özelleştirin.

- Editörünüz birden fazla görünümü destekleyecek mi? Düzenleyicinizin görünümlerinin varsayılan düzenleyiciyle aynı anda görünür olmasını istiyorsanız, birden çok görünümü desteklemeniz gerekir.

   Düzenleyicinizin birden çok görünümü desteklemesi gerekiyorsa, düzenleyicinin belge verileri ve belge görünümü nesneleri ayrı nesneler olmalıdır. Daha fazla bilgi için [bkz.](../extensibility/supporting-multiple-document-views.md)

   Düzenleyiciniz birden çok görünümü destekliyorsa, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] belge veri nesneniz için<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> temel düzenleyicinin metin arabelleği uygulamasını (nesnesi) kullanmayı planlıyor musunuz? Diğer bir şey, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editör görünümünüzü çekirdek editörle yan yana desteklemek istiyor musunuz? Bunu yapmak için yeteneği formlar tasarımcının temelidir ...

- Harici bir editör barındırmanız gerekiyorsa, editör içine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]gömülü olabilir mi?

   Katıştırılmış sayılsa, dış düzenleyici için bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> ana bilgisayar <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> penceresi oluşturmalı ve `DP_External`ardından yöntemi aramalı ve numaralandırma değerini . Düzenleyici katıştırılamazsa, IDE otomatik olarak bunun için ayrı bir pencere oluşturur.

## <a name="in-this-section"></a>Bu Bölümde

[Walkthrough: Özel bir düzenleyici oluşturma](../extensibility/walkthrough-creating-a-custom-editor.md)\
Özel bir düzenleyicinin nasıl oluşturulurmasını açıklar.

[İzole: Özel bir düzenleyiciye özellikler ekleme](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Özel bir düzenleyiciye nasıl özellik ekleyeceğini açıklar.

[Tasarımcı başlatma ve meta veri yapılandırması](../extensibility/designer-initialization-and-metadata-configuration.md)\
Bir tasarımcının nasıl başharfe atılanıntırılıyor.

[Tasarımcılara geri alım desteği](../extensibility/supplying-undo-support-to-designers.md)\
Tasarımcılar için geri geri verme desteğinin nasıl sağlayabileceğini açıklar.

[Özel editörlerde sözdizimi boyama](../extensibility/syntax-coloring-in-custom-editors.md)\
Çekirdek düzenleyicide ve özel editörlerde sözdizimi boyama arasındaki farkı açıklar.

[Özel düzenleyicilerde belge verileri ve belge görünümü](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Özel düzenleyicilerde belge verilerinin ve belge görünümlerinin nasıl uygulanacağını açıklar.

## <a name="related-sections"></a>İlgili bölümler

[Editörde eski arayüzler](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)\
Eski API ile çekirdek düzenleyiciye nasıl erişilenleri açıklar.

[Eski bir dil hizmeti geliştirme](../extensibility/internals/developing-a-legacy-language-service.md)\
Dil hizmetinin nasıl uygulanacağını açıklar.

[Visual Studio'nun diğer bölümlerini genişletin](../extensibility/extending-other-parts-of-visual-studio.md)\
Geri kalanıyla eşleşen ui öğelerinin [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]nasıl oluşturulacak larını açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
