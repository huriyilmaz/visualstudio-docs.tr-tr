---
title: Özel Parametreler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd52a49daa7d57a21d8cb0896f7108efa09e32b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708941"
---
# <a name="custom-parameters"></a>Özel parametreler
Özel parametreler, sihirbaz başladıktan sonra sihirbazın çalışmasını denetler. İlgili *.vsz* dosyası, tümleşik geliştirme ortamı (IDE) tarafından paketlenir ve sihirbaz başlatıldığında bir dizi dize olarak sihirbaza geçirilen kullanıcı tanımlı parametreler dizisi sağlar. Sihirbaz daha sonra dizeleri dizi parses ve sihirbazın gerçek çalışmasını denetlemek için bilgileri kullanır. Bu şekilde, sihirbaz *.vsz* dosyasının içeriğine bağlı olarak işlevselliği özelleştirebilir.

 Bağlam parametreleri, diğer taraftan, sihirbaz başlatıldığında projenin durumunu tanımlar. Daha fazla bilgi için [Bağlam parametrelerine](../../extensibility/internals/context-parameters.md)bakın.

 Aşağıda özel parametreleri olan bir *.vsz* dosyası örneği verilmiştir:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 *.vsz* dosyasının yazarı parametrelerin değerlerini ekler. Bir kullanıcı **Dosya** menüsünde **Yeni Proje** veya Yeni **Öğe Ekle'yi** seçtiğinde veya **Solution Explorer'daki**bir projeyi sağ tıklatarak, IDE bu değerleri bir dizi dize halinde toplar. IDE daha sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> bayrak kümesiyle projenin yöntemini çağırır ve <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> proje sihirbazı çalıştırmak ve sonucu döndürmekten sorumlu yöntemi çağırır.

 Sihirbaz, dizeleri dizi ayrıştırma ve dizeleri uygun şekilde hareket sorumludur. Bu şekilde, özel parametreler uygulayarak çeşitli işlevler gerçekleştiren bir sihirbaz oluşturabilirsiniz. Başka bir deyişle, bir sihirbazın üç farklı *.vsz* dosyası olabilir. Her dosya, sihirbazın çeşitli durumlardaki davranışını denetlemek için farklı özel parametreler kümelerinden geçer.

 Daha fazla bilgi için [Sihirbaz (.vsz) dosyasına](../../extensibility/internals/wizard-dot-vsz-file.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Bağlam parametreleri](../../extensibility/internals/context-parameters.md)
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Sihirbaz (.vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
