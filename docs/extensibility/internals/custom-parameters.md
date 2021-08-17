---
title: Özel parametreler | Microsoft Docs
description: Bir sihirbaz başladıktan sonra bir. vsz dosyasını değiştirerek sihirbazın çalışmasını denetleyen özel parametreler oluşturmayı öğrenin.
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
ms.openlocfilehash: ec6cefad7714952e150a940e44c99741d6a9b98ed2267d38cab1651c69932b78
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448136"
---
# <a name="custom-parameters"></a>Özel parametreler
Özel parametreler sihirbaz başladıktan sonra sihirbazın işlemini denetler. İlgili bir *. vsz* dosyası, tümleşik geliştirme ORTAMı (IDE) tarafından paketlenmiş ve sihirbaz başlatıldığında dize dizisi olarak sihirbaza geçilen Kullanıcı tanımlı parametrelerin dizisini sağlar. Sihirbaz daha sonra dizeler dizisini ayrıştırır ve sihirbazın gerçek işlemini denetlemek için bu bilgileri kullanır. Bu şekilde, bir sihirbaz *. vsz* dosyasının içeriğine bağlı olarak işlevselliği özelleştirebilir.

 Bağlam parametreleri, diğer yandan, sihirbaz başlatıldığında projenin durumunu tanımlar. Daha fazla bilgi için bkz. [Bağlam parametreleri](../../extensibility/internals/context-parameters.md).

 Özel parametrelere sahip bir *. vsz* dosyasının örneği aşağıda verilmiştir:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 *. Vsz* dosyasının yazarı parametre değerlerini ekler. kullanıcı **yeni Project** **seçtiğinde veya** **dosya** menüsünde bir projeye sağ tıklanarak **Çözüm Gezgini**, ıde bu değerleri bir dizeler dizisine toplar. Daha sonra IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> bayrak kümesiyle projenin yöntemini çağırır <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> ve proje, <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> Sihirbazı çalıştırmaktan ve sonucu döndürmekten sorumlu yöntemi çağırır.

 Sihirbaz, dizelerin dizisini ayrıştırmaktan ve dizilerin uygun şekilde davranmasından sorumludur. Bu şekilde, özel parametreler uygulayarak çeşitli işlevler gerçekleştiren bir sihirbaz oluşturabilirsiniz. Diğer bir deyişle, bir sihirbaz üç farklı *. vsz* dosyasına sahip olabilir. Her dosya, sihirbazın çeşitli durumlarda davranışını denetlemek için farklı özel parametre kümeleri geçirir.

 Daha fazla bilgi için bkz. [sihirbaz (. vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md).

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Bağlam parametreleri](../../extensibility/internals/context-parameters.md)
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Sihirbaz (. vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
