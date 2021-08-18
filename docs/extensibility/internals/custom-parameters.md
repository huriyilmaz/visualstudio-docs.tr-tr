---
title: Özel Parametreler | Microsoft Docs
description: Bir .vsz dosyasını değiştirerek, sihirbaz başlatıldıktan sonra sihirbazın işlemi kontrol altına alan özel parametreler oluşturma hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3251b657d269a313cc160d041138aec0dba51235
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063531"
---
# <a name="custom-parameters"></a>Özel parametreler
Sihirbaz başlatıldıktan sonra sihirbazın çalışması özel parametreler tarafından kontrol altına alındı. İlgili *bir .vsz* dosyası, tümleşik geliştirme ortamı (IDE) tarafından paketlenmiş ve sihirbaz başlatılana dize dizisi olarak geçirilen kullanıcı tanımlı parametreler dizisi sağlar. Sihirbaz daha sonra dize dizisini ayrıştırıyor ve sihirbazın gerçek işlemlerini kontrol etmek için bilgileri kullanıyor. Bu şekilde sihirbaz, *.vsz* dosyasının içeriğine bağlı olarak işlevselliği özelleştirilebilir.

 Diğer taraftan bağlam parametreleri, sihirbaz başlatılana kadar projenin durumunu tanımlar. Daha fazla bilgi için [bkz. Bağlam parametreleri.](../../extensibility/internals/context-parameters.md)

 Aşağıda, özel parametreleri olan *bir .vsz* dosyası örneği ve ardından ve bir örnek yer almaktadır:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 *.vsz dosyasının yazarı* parametrelerin değerlerini ekler. Kullanıcı Dosya menüsünde **yeni** Project Ekle'yi veya Çözüm Gezgini'de bir projeye sağ tıklayarak Yeni Öğe Ekle'yi seçerse, IDE bu değerleri bir dize dizisine toplar.   Ardından IDE, bayrak kümesiyle projenin yöntemini, proje ise sihirbazı çalıştırarak sonucu döndüren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> yöntemini <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> çağırarak.

 Sihirbaz, dize dizisini ayrıştırmak ve dizeler üzerinde uygun şekilde hareket etme sorumluluğundadır. Bu şekilde, özel parametreler kullanarak çeşitli işlevleri gerçekleştiren bir sihirbaz oluşturabilirsiniz. Başka bir deyişle, bir sihirbazın üç farklı *.vsz dosyası* olabilir. Her dosya, sihirbazın davranışını çeşitli durumlarda kontrol etmek için farklı özel parametre kümeleri iletir.

 Daha fazla bilgi için [bkz. Sihirbaz (.vsz) dosyası.](../../extensibility/internals/wizard-dot-vsz-file.md)

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Bağlam parametreleri](../../extensibility/internals/context-parameters.md)
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Sihirbaz (.vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
