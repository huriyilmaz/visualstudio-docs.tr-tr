---
title: Özel Editörlerde Belge Verileri ve Belge Görünümü | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04e89194ff09bc273294246cc25718c999daf70f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712139"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Özel düzenleyicilerde belge verileri ve belge görünümü
Özel bir düzenleyici iki bölümden oluşur: belge veri nesnesi ve belge görünümü nesnesi. Adların da belirttiği gibi, belge veri nesnesi görüntülenecek metin verilerini temsil eder. Benzer şekilde, belge görünümü nesnesi (veya "görünüm"), belge veri nesnesini görüntülemek için bir veya daha fazla pencereyi temsil eder.

## <a name="document-data-object"></a>Belge veri nesnesi
 Belge veri nesnesi, metin arabelleğindeki metnin veri gösterimidir. Belge metnini ve diğer bilgileri depolayan bir COM nesnesidir. Belge veri nesnesi, belge kalıcılığını da işler ve verilerinin birden çok kez görüntülenmelerini sağlar. Daha fazla bilgi için bkz.

 <xref:EnvDTE80.Window2.DocumentData%2A>ve [Belge Windows](../extensibility/internals/document-windows.md).

 Özel düzenleyiciler ve tasarımcılar <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> nesneyi veya kendi özel arabelleklerini kullanmayı seçebilirler. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>standart bir düzenleyici için basitleştirilmiş katıştırma modelini izler, birden çok görünümü destekler ve birden çok görünümü yönetmek için kullanılan olay arabirimleri sağlar.

## <a name="document-view-object"></a>Belge görünümü nesnesi
 Kodu ve diğer metni görüntüleyen bir pencere, belge görünümü veya görünümü olarak bilinir. Bir düzenleyici oluşturduğunuzda, tek bir pencerede metnin görüntülendiği tek bir görünüm seçebilirsiniz. Veya birden fazla pencerede metnin görüntülendiği birden çok görünüm seçebilirsiniz. Seçiminiz başvurunuza bağlıdır. Örneğin, yan yana düzenlemeye ihtiyacınız varsa, birden çok görünüm seçersiniz. Her görünüm, tümleşik geliştirme ortamının (IDE) çalışan belge tablosundaki (RDT) bir girişle ilişkilidir. Görünüm pencereleri bir projeye <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> veya nesneye aittir.

 Düzenleyiciniz bir belge veri nesnesinin birden çok görünümünü destekliyorsa, belge verileriniz ve belge görünümü nesnelerinizin ayrı olması gerekir. Aksi takdirde, birlikte gruplandırılabilir. Daha fazla bilgi için [bkz.](../extensibility/supporting-multiple-document-views.md)

 IDE, çalışan belge tablosundaki her giriş için bir öğe tanımlayıcısını (ItemID) eşleştirerek olaylarla ilgili görünümleri (örneğin, belge içeren bir çözüm kapatıldığında) bildirimde eder. Bu konuda daha fazla bilgi [için, Bkz. Çalışma belge tablosu.](../extensibility/internals/running-document-table.md)

 Özel bir düzenleyici için görünüm oluşturmak için iki seçenek vardır. Bunlardan biri, görünümün ActiveX denetimi veya belge veri nesnesi kullanılarak bir pencerede barındırıldığı yerinde etkinleştirme modelidir. İkincisi, görünümün pencere komutları tarafından [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] barındırıldığı ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> uygulandığı basitleştirilmiş katıştırma modelidir. Yerinde etkinleştirme modeli hakkında daha fazla bilgi için [yerinde etkinleştirme'ye](/visualstudio/misc/in-place-activation?view=vs-2015)bakın. Basitleştirilmiş katıştırma modeli hakkında bilgi için [basitleştirilmiş katıştırma'ya](../extensibility/simplified-embedding.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Birden çok belge görüntülemeyi destekleme](../extensibility/supporting-multiple-document-views.md)
- [Basitleştirilmiş gömme](../extensibility/simplified-embedding.md)
- [Nasıl kullanılır: Belge verilerine görünüm ekleme](../extensibility/how-to-attach-views-to-document-data.md)
- [Belge kilidi tutucu yönetimi](../extensibility/document-lock-holder-management.md)
- [Tek ve çoklu sekme görünümleri](../extensibility/single-and-multi-tab-views.md)
- [Standart bir belgeyi kaydetme](../extensibility/internals/saving-a-standard-document.md)
- [Kalıcılık ve çalışan belge tablosu](../extensibility/internals/persistence-and-the-running-document-table.md)
- [Projede dosyayı hangi düzenleyicinin açtığını belirleme](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)
