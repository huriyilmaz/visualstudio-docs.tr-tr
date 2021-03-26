---
title: Özel düzenleyiciler ve tasarımcılar oluşturma | Microsoft Docs
description: 'Visual Studio IDE tarafından barındırılabilen farklı Düzenleyici türleri hakkında bilgi edinin: Çekirdek Düzenleyici, özel düzenleyiciler, dış düzenleyiciler ve tasarımcılar.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2882cfa103627672e5c96a0e3d4b2a23b4b4ba9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055784"
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
 Özel bir düzenleyici, özelleştirilmiş koşullarda çalışmak üzere tasarlanan bir düzenleyicidir. Örneğin, işlevi, Microsoft Exchange Server gibi belirli bir depoya veri okuma ve yazma işlemi olan bir düzenleyici oluşturabilirsiniz. Yalnızca birkaç özel komuta sahip bir düzenleyici istiyorsanız, yalnızca proje türüyle çalışacak bir düzenleyici istiyorsanız özel bir düzenleyici seçin. Ancak, kullanıcıların standart projeleri düzenlemek için özel bir düzenleyici kullanabilebileceğine unutmayın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 Özel bir düzenleyici bir düzenleyici fabrikası kullanabilir ve kayıt defterine Düzenleyici hakkında bilgi ekleyebilir. Ancak, özel düzenleyiciyle ilişkilendirilen proje türü özel düzenleyiciyi başka yollarla oluşturabilir.

 Özel bir düzenleyici, bir görünümü uygulamak için yerinde etkinleştirme ya da Basitleştirilmiş ekleme kullanabilir.

### <a name="external-editors"></a>Dış düzenleyiciler
 Dış düzenleyiciler, Visual Studio ile tümleştirilen, Microsoft Word, Notepad veya Microsoft FrontPage gibi düzenleyicilerlerdir. Örneğin, VSPackage 'ınızdan metin aktarıyorsanız bu tür bir düzenleyiciyi çağırabilirsiniz. Dış düzenleyiciler kendilerini kaydeder ve Visual Studio 'Nun dışında kullanılabilir. Harici bir düzenleyiciyi çağırdığınızda ve bir konak penceresine katıştırılabildiğinden, IDE 'deki bir pencerede görüntülenir. Aksi takdirde, IDE bunun için ayrı bir pencere oluşturur.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>Yöntemi, sabit listesini kullanarak belge önceliğini ayarlar <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> . `DP_External`Değer belirtilmişse, dosya harici bir düzenleyici tarafından açılabilir.

## <a name="editor-design-decisions"></a>Düzenleyici tasarım kararları
 Aşağıdaki tasarım soruları, uygulamanıza en uygun düzenleyici türünü seçmenize yardımcı olur:

- Uygulamanız verileri dosyalara kaydetmek mi, yoksa mı? Verileri dosyalara kaydedecektir, özel veya standart biçimde olacaktır mi?

   Standart bir dosya biçimi kullanırsanız, projenize ek olarak diğer proje türleri de açabilir ve verileri okuyabilir/yazabilir. Ancak, özel bir dosya biçimi kullanırsanız, yalnızca proje türü verileri açabilir ve bunlara okuyabilir/yazabilir.

   Projeniz dosyaları kullanıyorsa, standart düzenleyiciyi özelleştirmeniz gerekir. Projeniz dosyaları kullanmıyorsa, ancak bir veritabanı veya başka bir depodaki öğeleri kullanıyorsa, özel bir düzenleyici oluşturmanız gerekir.

- Düzenleyicinizde ActiveX denetimleri barındırmı gerekiyor?

   Düzenleyiciniz ActiveX denetimleri barındırıyorsa, yerinde [etkinleştirme](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015)' de açıklandığı gibi bir yerinde etkinleştirme Düzenleyicisi uygulayın. ActiveX denetimleri barındırmadığından, Basitleştirilmiş bir katıştırma düzenleyicisi kullanın veya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] varsayılan düzenleyiciyi özelleştirin.

- Düzenleyiciniz birden fazla görünümü destekliyor mu? Düzenleyicinizdeki görünümlerin varsayılan düzenleyiciyle aynı anda görünür olmasını istiyorsanız birden çok görünümü desteklemeniz gerekir.

   Düzenleyicinin birden çok görünümü desteklemesi gerekiyorsa, düzenleyicinin belge verileri ve belge görünümü nesneleri ayrı nesneler olmalıdır. Daha fazla bilgi için bkz. [birden çok belge görünümünü destekleme](../extensibility/supporting-multiple-document-views.md).

   Düzenleyiciniz birden çok görünümü destekliyorsa, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] belge veri nesneniz için çekirdek düzenleyicinin metin arabelleği uygulamasını (nesne) kullanmayı planlıyorsunuz musunuz <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> ? Diğer bir deyişle, çekirdek düzenleyiciyle düzenleyici görünümünüzü yan yana desteklemek istiyor musunuz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ? Bunu yapma özelliği, form tasarımcısının temelini oluşturur.

- Harici bir düzenleyiciyi barındırmanıza ihtiyacınız varsa, düzenleyici içine gömülebilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mi?

   Katıştırılabiliyorsanız, dış düzenleyici için bir konak penceresi oluşturmanız ve sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> yöntemi çağırıp <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> numaralandırma değerini olarak ayarlamanız gerekir `DP_External` . Düzenleyici katıştırılamayacağını içeriyorsa, IDE otomatik olarak ayrı bir pencere oluşturur.

## <a name="in-this-section"></a>Bu Bölümde

[İzlenecek yol: özel bir düzenleyici oluşturma](../extensibility/walkthrough-creating-a-custom-editor.md)\
Özel bir düzenleyicinin nasıl oluşturulacağını açıklar.

[İzlenecek yol: özel düzenleyiciye özellikler ekleme](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Özel bir düzenleyiciye özelliklerin nasıl ekleneceğini açıklar.

[Tasarımcı başlatması ve meta veri yapılandırması](../extensibility/designer-initialization-and-metadata-configuration.md)\
Bir tasarımcının nasıl başlatılacağını açıklar.

[Tasarımcı için geri alma desteğini sağlama](../extensibility/supplying-undo-support-to-designers.md)\
Tasarımcılar için geri alma desteğinin nasıl sağlanacağını açıklar.

[Özel düzenleyicilerde söz dizimi renklendirmesi](../extensibility/syntax-coloring-in-custom-editors.md)\
Çekirdek düzenleyicide ve özel düzenleyicilerde sözdizimi renklendirme arasındaki farkı açıklar.

[Özel düzenleyicilerde belge verileri ve belge görünümü](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Belge verilerinin ve belge görünümlerinin özel düzenleyicilerde nasıl uygulanacağını açıklar.

## <a name="related-sections"></a>İlgili bölümler

[Düzenleyicideki eski arabirimler](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015)\
Çekirdek düzenleyiciye, eski API 'nin yoluyla nasıl erişebileceğinizi açıklar.

[Eski dil hizmeti geliştirme](../extensibility/internals/developing-a-legacy-language-service.md)\
Bir dil hizmetinin nasıl uygulanacağını açıklar.

[Visual Studio 'nun diğer kısımlarını genişletme](../extensibility/extending-other-parts-of-visual-studio.md)\
Geri kalanı ile eşleşen kullanıcı arabirimi öğelerinin nasıl oluşturulacağını açıklar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
