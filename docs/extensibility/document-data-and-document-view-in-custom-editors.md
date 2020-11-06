---
title: Özel düzenleyicilerde belge verileri ve belge görünümü | Microsoft Docs
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
ms.openlocfilehash: 6d4b14558a435d6ad9da32726508d81185961410
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414470"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Özel düzenleyicilerde belge verileri ve belge görünümü
Özel bir düzenleyici iki bölümden oluşur: bir belge veri nesnesi ve bir belge görünümü nesnesi. Adlar gösterildiğinde belge verileri nesnesi görüntülenecek metin verilerini temsil eder. Benzer şekilde, belge görünümü nesnesi (veya "Görünüm"), belge veri nesnesinin görüntüleneceği bir veya daha fazla pencere temsil eder.

## <a name="document-data-object"></a>Belge veri nesnesi
 Belge veri nesnesi, metin arabelleğindeki metnin veri gösterimidir. Belge metnini ve diğer bilgileri depolayan bir COM nesnesidir. Belge verileri nesnesi, belge kalıcılığını da işler ve verilerinin birden çok görünümünü sunar. Daha fazla bilgi için bkz.

 <xref:EnvDTE80.Window2.DocumentData%2A> ve [belge pencereleri](../extensibility/internals/document-windows.md).

 Özel düzenleyiciler ve tasarımcılar, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> nesneyi veya kendi özel arabelleğini kullanmayı tercih edebilir. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Standart bir düzenleyici için Basitleştirilmiş ekleme modelini izler, birden fazla görünümü destekler ve birden çok görünümü yönetmek için kullanılan olay arabirimlerini sağlar.

## <a name="document-view-object"></a>Belge görünümü nesnesi
 Kodu ve diğer metinleri görüntüleyen bir pencere, belge görünümü veya görünüm olarak bilinir. Bir düzenleyici oluşturduğunuzda, metnin tek bir pencerede görüntüleneceği tek bir görünüm seçebilirsiniz. Ya da metnin birden çok pencerede görüntüleneceği birden çok görünüm seçebilirsiniz. Seçiminiz uygulamanıza bağlıdır. Örneğin, yan yana düzenlenmesine ihtiyacınız varsa, birden çok görünüm seçersiniz. Her görünüm, tümleşik geliştirme ortamının (IDE) çalışan belge tablosu 'nda (RDT) bir girdiyle ilişkilendirilir. Windows görüntüleme, bir projeye veya nesneye aittir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .

 Düzenleyiciniz bir belge veri nesnesinin birden çok görünümünü destekliyorsa, belge verileri ve belge görünümü nesneleriniz ayrı olmalıdır. Aksi takdirde, birlikte gruplanabilir. Daha fazla bilgi için bkz. [birden çok belge görünümünü destekleme](../extensibility/supporting-multiple-document-views.md).

 IDE, çalışan belge tablosundaki her girdinin bir öğe tanımlayıcısını (ItemId) eşleştirerek olayları (örneğin, bir belge içeren bir çözüm kapatıldığında) hakkında görünümler bildirir. Bu konuda daha fazla bilgi için bkz. [çalışma belge tablosu](../extensibility/internals/running-document-table.md).

 Özel bir düzenleyici için bir görünüm oluşturmak için iki seçenek vardır. Bunlardan biri, görünümün bir ActiveX denetimi veya belge veri nesnesi kullanılarak bir pencerede barındırıldığı yerinde etkinleştirme modelidir. İkincisi, görünümün tarafından barındırıldığı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Pencere komutlarını işlemek için uygulandığı Basitleştirilmiş ekleme modelidir. Yerinde etkinleştirme modeli hakkında daha fazla bilgi için bkz. [yerinde etkinleştirme](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015). Basitleştirilmiş ekleme modeli hakkında daha fazla bilgi için bkz. [Basitleştirilmiş ekleme](../extensibility/simplified-embedding.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Çoklu belge görünümlerini destekleme](../extensibility/supporting-multiple-document-views.md)
- [Basitleştirilmiş ekleme](../extensibility/simplified-embedding.md)
- [Nasıl yapılır: belge verilerine görünümler Iliştirme](../extensibility/how-to-attach-views-to-document-data.md)
- [Belge kilit tutucusu yönetimi](../extensibility/document-lock-holder-management.md)
- [Tek ve çok sekme görünümleri](../extensibility/single-and-multi-tab-views.md)
- [Standart bir belge Kaydet](../extensibility/internals/saving-a-standard-document.md)
- [Kalıcılık ve çalışan belge tablosu](../extensibility/internals/persistence-and-the-running-document-table.md)
- [Bir projede dosya açan düzenleyiciyi belirleme](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)