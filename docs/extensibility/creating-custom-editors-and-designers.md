---
title: Özel düzenleyiciler ve tasarımcılar oluşturma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a6cb0d70566eaabb2ba37cb209041e03684c958
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73568872"
---
# <a name="create-custom-editors-and-designers"></a>Özel düzenleyiciler ve tasarımcılar oluşturma

Visual Studio tümleşik geliştirme ortamı (IDE) farklı düzenleyici türlerini barındırabilir:

- Visual Studio temel Düzenleyicisi

- Özel düzenleyiciler

- Dış düzenleyiciler

- Tasarımcılar

Aşağıdaki bilgiler, ihtiyacınız olan düzenleyicinin türünü seçmenize yardımcı olur.

## <a name="types-of-editor"></a>Düzenleyici türleri

Visual Studio çekirdek Düzenleyicisi hakkında daha fazla bilgi için bkz. [düzenleyiciyi ve dil hizmetlerini genişletme](../extensibility/extending-the-editor-and-language-services.md).

### <a name="custom-editors"></a>Özel düzenleyiciler
 Özel bir düzenleyici, özelleştirilmiş koşullarda çalışmak üzere tasarlanan bir düzenleyicidir. Örneğin, işlevi, Microsoft Exchange Server gibi belirli bir depoya veri okuma ve yazma işlemi olan bir düzenleyici oluşturabilirsiniz. Yalnızca birkaç özel komuta sahip bir düzenleyici istiyorsanız, yalnızca proje türüyle çalışacak bir düzenleyici istiyorsanız özel bir düzenleyici seçin. Ancak, kullanıcıların standart [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projelerini düzenlemek için özel bir düzenleyici kullanabilebileceğine unutmayın.

 Özel bir düzenleyici bir düzenleyici fabrikası kullanabilir ve kayıt defterine Düzenleyici hakkında bilgi ekleyebilir. Ancak, özel düzenleyiciyle ilişkilendirilen proje türü özel düzenleyiciyi başka yollarla oluşturabilir.

 Özel bir düzenleyici, bir görünümü uygulamak için yerinde etkinleştirme ya da Basitleştirilmiş ekleme kullanabilir.

### <a name="external-editors"></a>Dış düzenleyiciler
 Dış düzenleyiciler, Visual Studio ile tümleştirilen, Microsoft Word, Notepad veya Microsoft FrontPage gibi düzenleyicilerlerdir. Örneğin, VSPackage 'ınızdan metin aktarıyorsanız bu tür bir düzenleyiciyi çağırabilirsiniz. Dış düzenleyiciler kendilerini kaydeder ve Visual Studio 'Nun dışında kullanılabilir. Harici bir düzenleyiciyi çağırdığınızda ve bir konak penceresine katıştırılabildiğinden, IDE 'deki bir pencerede görüntülenir. Aksi takdirde, IDE bunun için ayrı bir pencere oluşturur.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> yöntemi, <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> sabit listesini kullanarak belge önceliğini ayarlar. `DP_External` değeri belirtilmişse, dosya harici bir düzenleyici tarafından açılabilir.

## <a name="editor-design-decisions"></a>Düzenleyici tasarım kararları
 Aşağıdaki tasarım soruları, uygulamanıza en uygun düzenleyici türünü seçmenize yardımcı olur:

- Uygulamanız verileri dosyalara kaydetmek mi, yoksa mı? Verileri dosyalara kaydedecektir, özel veya standart biçimde olacaktır mi?

   Standart bir dosya biçimi kullanırsanız, projenize ek olarak diğer proje türleri de açabilir ve verileri okuyabilir/yazabilir. Ancak, özel bir dosya biçimi kullanırsanız, yalnızca proje türü verileri açabilir ve bunlara okuyabilir/yazabilir.

   Projeniz dosyaları kullanıyorsa, standart düzenleyiciyi özelleştirmeniz gerekir. Projeniz dosyaları kullanmıyorsa, ancak bir veritabanı veya başka bir depodaki öğeleri kullanıyorsa, özel bir düzenleyici oluşturmanız gerekir.

- Düzenleyicinizde ActiveX denetimleri barındırmı gerekiyor?

   Düzenleyiciniz ActiveX denetimleri barındırıyorsa, yerinde [etkinleştirme](/visualstudio/misc/in-place-activation?view=vs-2015)' de açıklandığı gibi bir yerinde etkinleştirme Düzenleyicisi uygulayın. ActiveX denetimlerini barındırmadığından, Basitleştirilmiş bir katıştırma düzenleyicisi kullanın veya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] varsayılan düzenleyiciyi özelleştirin.

- Düzenleyiciniz birden fazla görünümü destekliyor mu? Düzenleyicinizdeki görünümlerin varsayılan düzenleyiciyle aynı anda görünür olmasını istiyorsanız birden çok görünümü desteklemeniz gerekir.

   Düzenleyicinin birden çok görünümü desteklemesi gerekiyorsa, düzenleyicinin belge verileri ve belge görünümü nesneleri ayrı nesneler olmalıdır. Daha fazla bilgi için bkz. [birden çok belge görünümünü destekleme](../extensibility/supporting-multiple-document-views.md).

   Düzenleyiciniz birden çok görünümü destekliyorsa, belge verileri nesneniz için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çekirdek Düzenleyicisi 'nin metin arabellek uygulamasını (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> nesnesi) kullanmayı planlıyorsunuz musunuz? Diğer bir deyişle, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çekirdek Düzenleyicisi ile düzenleyici görünümünüzü yan yana desteklemek istiyor musunuz? Bunu yapma özelliği, form tasarımcısının temelini oluşturur.

- Harici bir düzenleyiciyi barındırmanıza ihtiyacınız varsa, düzenleyici [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]içine katıştırılabilir mi?

   Katıştırılabiliyorsanız, dış düzenleyici için bir konak penceresi oluşturmanız ve ardından <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> yöntemini çağırmanız ve <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> numaralandırma değerini `DP_External`olarak ayarlamanız gerekir. Düzenleyici katıştırılamayacağını içeriyorsa, IDE otomatik olarak ayrı bir pencere oluşturur.

## <a name="in-this-section"></a>Bu Bölümde

[Izlenecek yol: özel bir düzenleyici\ oluşturma](../extensibility/walkthrough-creating-a-custom-editor.md)
Özel bir düzenleyicinin nasıl oluşturulacağını açıklar.

[Izlenecek yol: özel bir düzenleyiciye özellikler ekleme](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Özel bir düzenleyiciye özelliklerin nasıl ekleneceğini açıklar.

[Tasarımcı başlatma ve meta veri yapılandırma](../extensibility/designer-initialization-and-metadata-configuration.md)\
Bir tasarımcının nasıl başlatılacağını açıklar.

[Tasarımcılara geri alma desteği sağlayın](../extensibility/supplying-undo-support-to-designers.md)\
Tasarımcılar için geri alma desteğinin nasıl sağlanacağını açıklar.

[Özel düzenleyicilerde söz dizimi renklendirmesi](../extensibility/syntax-coloring-in-custom-editors.md)\
Çekirdek düzenleyicide ve özel düzenleyicilerde sözdizimi renklendirme arasındaki farkı açıklar.

[Özel düzenleyicilerde belge verilerini ve belge görünümünü](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Belge verilerinin ve belge görünümlerinin özel düzenleyicilerde nasıl uygulanacağını açıklar.

## <a name="related-sections"></a>İlgili bölümler

[Düzenleyicideki eski arabirimler](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)\
Çekirdek düzenleyiciye, eski API 'nin yoluyla nasıl erişebileceğinizi açıklar.

[Eski dil hizmeti\ geliştirme](../extensibility/internals/developing-a-legacy-language-service.md)
Bir dil hizmetinin nasıl uygulanacağını açıklar.

[Visual Studio 'nun diğer kısımlarını genişletme](../extensibility/extending-other-parts-of-visual-studio.md)\
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]geri kalanı ile eşleşen kullanıcı arabirimi öğelerinin nasıl oluşturulacağını açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>