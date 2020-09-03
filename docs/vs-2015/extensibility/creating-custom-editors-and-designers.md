---
title: Özel düzenleyiciler ve tasarımcılar oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
caps.latest.revision: 32
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc94d11a5ed118f0133657ebf5b966623a199d64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197416"
---
# <a name="creating-custom-editors-and-designers"></a>Özel Düzenleyiciler ve Tasarımcılar Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio tümleşik geliştirme ortamı (IDE) farklı düzenleyici türlerini barındırabilir:  
  
- Visual Studio temel Düzenleyicisi  
  
- Özel düzenleyiciler  
  
- Dış düzenleyiciler  
  
- Tasarımcılar  
  
  Aşağıdaki bilgiler, ihtiyacınız olan düzenleyicinin türünü seçmenize yardımcı olur.  
  
## <a name="types-of-editor"></a>Düzenleyici türleri  
 Visual Studio çekirdek Düzenleyicisi hakkında daha fazla bilgi için bkz. [düzenleyiciyi ve dil hizmetlerini genişletme](../extensibility/extending-the-editor-and-language-services.md).  
  
##### <a name="custom-editors"></a>Özel düzenleyiciler  
 Özel bir düzenleyici, özelleştirilmiş koşullarda çalışmak üzere tasarlanan bir düzenleyicidir. Örneğin, işlevi, Microsoft Exchange Server gibi belirli bir depoya veri okuma ve yazma işlemi olan bir düzenleyici oluşturabilirsiniz. Yalnızca birkaç özel komuta sahip bir düzenleyici istiyorsanız, yalnızca proje türüyle çalışacak bir düzenleyici istiyorsanız özel bir düzenleyici seçin. Ancak, kullanıcıların standart projeleri düzenlemek için özel bir düzenleyici kullanabilebileceğine unutmayın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 Özel bir düzenleyici bir düzenleyici fabrikası kullanabilir ve kayıt defterine Düzenleyici hakkında bilgi ekleyebilir. Ancak, özel düzenleyiciyle ilişkilendirilen proje türü özel düzenleyiciyi başka yollarla oluşturabilir.  
  
 Özel bir düzenleyici, bir görünümü uygulamak için yerinde etkinleştirme ya da Basitleştirilmiş ekleme kullanabilir.  
  
##### <a name="external-editors"></a>Dış düzenleyiciler  
 Dış düzenleyiciler, Visual Studio ile tümleştirilen, Microsoft Word, Notepad veya Microsoft FrontPage gibi düzenleyicilerlerdir. Örneğin, VSPackage 'ınızdan metin aktarıyorsanız bu tür bir düzenleyiciyi çağırabilirsiniz. Dış düzenleyiciler kendilerini kaydeder ve Visual Studio 'Nun dışında kullanılabilir. Harici bir düzenleyiciyi çağırdığınızda ve bir konak penceresine katıştırılabildiğinden, IDE 'deki bir pencerede görüntülenir. Aksi takdirde, IDE bunun için ayrı bir pencere oluşturur.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>Yöntemi, sabit listesini kullanarak belge önceliğini ayarlar <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> . `DP_External`Değer belirtilmişse, dosya harici bir düzenleyici tarafından açılabilir.  
  
## <a name="editor-design-decisions"></a>Düzenleyici tasarım kararları  
 Aşağıdaki tasarım soruları, uygulamanıza en uygun düzenleyici türünü seçmenize yardımcı olur:  
  
- Uygulamanız verileri dosyalara kaydetmek mi, yoksa mı? Verileri dosyalara kaydedecektir, özel veya standart biçimde olacaktır mi?  
  
     Standart bir dosya biçimi kullanırsanız, projenize ek olarak diğer proje türleri de açabilir ve verileri okuyabilir/yazabilir. Ancak, özel bir dosya biçimi kullanırsanız, yalnızca proje türü verileri açabilir ve bunlara okuyabilir/yazabilir.  
  
     Projeniz dosyaları kullanıyorsa, standart düzenleyiciyi özelleştirmeniz gerekir. Projeniz dosyaları kullanmıyorsa, ancak bir veritabanı veya başka bir depodaki öğeleri kullanıyorsa, özel bir düzenleyici oluşturmanız gerekir.  
  
- Düzenleyicinizde ActiveX denetimleri barındırmı gerekiyor?  
  
     Düzenleyiciniz ActiveX denetimleri barındırıyorsa, yerinde [etkinleştirme](../misc/in-place-activation.md)' de açıklandığı gibi bir yerinde etkinleştirme Düzenleyicisi uygulayın. ActiveX denetimleri barındırmadığından, Basitleştirilmiş bir katıştırma düzenleyicisi kullanın veya [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] varsayılan düzenleyiciyi özelleştirin.  
  
- Düzenleyiciniz birden fazla görünümü destekliyor mu? Düzenleyicinizdeki görünümlerin varsayılan düzenleyiciyle aynı anda görünür olmasını istiyorsanız birden çok görünümü desteklemeniz gerekir.  
  
     Düzenleyicinin birden çok görünümü desteklemesi gerekiyorsa, düzenleyicinin belge verileri ve belge görünümü nesneleri ayrı nesneler olmalıdır. Daha fazla bilgi için bkz. [birden çok belge görünümünü destekleme](../extensibility/supporting-multiple-document-views.md).  
  
     Düzenleyiciniz birden çok görünümü destekliyorsa, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] belge veri nesneniz için çekirdek düzenleyicinin metin arabelleği uygulamasını (nesne) kullanmayı planlıyorsunuz musunuz <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> ? Diğer bir deyişle, çekirdek düzenleyiciyle düzenleyici görünümünüzü yan yana desteklemek istiyor musunuz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ? Bunu yapma özelliği, form tasarımcısının temelini oluşturur.  
  
- Harici bir düzenleyiciyi barındırmanıza ihtiyacınız varsa, düzenleyici içine gömülebilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mi?  
  
     Katıştırılabiliyorsanız, dış düzenleyici için bir konak penceresi oluşturmanız ve sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> yöntemi çağırıp <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> numaralandırma değerini olarak ayarlamanız gerekir `DP_External` . Düzenleyici katıştırılamayacağını içeriyorsa, IDE otomatik olarak ayrı bir pencere oluşturur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İzlenecek Yol: Özel Düzenleyici Oluşturma](../extensibility/walkthrough-creating-a-custom-editor.md)  
 Özel bir düzenleyicinin nasıl oluşturulacağını açıklar.  
  
 [İzlenecek Yol: Bir Özel Düzenleyiciye Özellik Ekleme](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 Özel bir düzenleyiciye özelliklerin nasıl ekleneceğini açıklar.  
  
 [Tasarımcıyı Başlatma ve Meta Verileri Yapılandırma](../extensibility/designer-initialization-and-metadata-configuration.md)  
 Bir tasarımcının nasıl başlatılacağını açıklar.  
  
 [Tasarımcılara Geri Alma Desteği Sağlama](../extensibility/supplying-undo-support-to-designers.md)  
 Tasarımcılar için geri alma desteğinin nasıl sağlanacağını açıklar.  
  
 [Özel Düzenleyicilerde Söz Dizimi Renklendirmesi](../extensibility/syntax-coloring-in-custom-editors.md)  
 Çekirdek düzenleyicide ve özel düzenleyicilerde sözdizimi renklendirme arasındaki farkı açıklar.  
  
 [Özel Düzenleyicilerde Belge Verileri ve Belge Görünümü](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 Belge verilerinin ve belge görünümlerinin özel düzenleyicilerde nasıl uygulanacağını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Düzenleyicideki Eski Arabirimler](../extensibility/legacy-interfaces-in-the-editor.md)  
 Çekirdek düzenleyiciye, eski API 'nin yoluyla nasıl erişebileceğinizi açıklar.  
  
 [Eski Dil Hizmeti Geliştirme](../extensibility/internals/developing-a-legacy-language-service.md)  
 Bir dil hizmetinin nasıl uygulanacağını açıklar.  
  
 [Visual Studio’nun Diğer Bölümlerini Genişletme](../extensibility/extending-other-parts-of-visual-studio.md)  
 Geri kalanı ile eşleşen kullanıcı arabirimi öğelerinin nasıl oluşturulacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
