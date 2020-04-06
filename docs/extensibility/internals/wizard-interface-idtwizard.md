---
title: Sihirbaz Arabirimi (IDTWizard) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb1c8d728a76097321e4e1f16640cab97599d6ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703270"
---
# <a name="wizard-interface-idtwizard"></a>Sihirbaz Arabirimi (IDTWizard)
Tümleşik geliştirme ortamı (IDE), sihirbazlarla iletişim kurmak için <xref:EnvDTE.IDTWizard> arabirimi kullanır. Sihirbazlar IDE yüklü olması için bu arabirimi uygulamak gerekir.

 <xref:EnvDTE.IDTWizard> Yöntem, <xref:EnvDTE.IDTWizard.Execute%2A> arabirimle ilişkili tek yöntemdir. Sihirbazlar bu yöntemi uygular ve IDE arabirimdeki yöntemi çağırır. Aşağıdaki örnek, yöntemin imzasını gösterir.

```
/* IDTWizard Method */
STDMETHOD(Execute)(THIS_
   /* [in] */ IDispatch *Application,
   /* [in] */ long hwndOwner,
   /* [in] */ SAFEARRAY * *ContextParams,
   /* [in] */ SAFEARRAY * *CustomParams,
   /* [out] [in] */ wizardResult *RetVal
   );
```

 Başlangıç mekanizması hem Yeni **Proje** hem de **Yeni Öğe Ekle** sihirbazları için benzer. Her birini başlatmak için, Dteinternal.h'de tanımlanan <xref:EnvDTE.IDTWizard> arabirimi çağırırsınız. Tek fark, arabirim çağrıldığında arabirime geçirilen bağlam ve özel parametreler kümesidir.

 Aşağıdaki bilgiler, <xref:EnvDTE.IDTWizard> sihirbazların [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE'de çalışmak için uygulaması gereken arabirimi açıklar. IDE sihirbazüzerinde <xref:EnvDTE.IDTWizard.Execute%2A> yöntemi çağırır ve aşağıdakileri aktarar:

- DTE nesnesi

     DTE nesnesi Otomasyon modelinin köküdür.

- Kod segmentinde gösterildiği gibi pencere iletişim kutusunun tutamacı, `hwndOwner ([in] long)`.

     Sihirbaz bunu `hwndOwner` sihirbaz iletişim kutusunun üst öğesi olarak kullanır.

- Kod segmentinde gösterildiği gibi SAFEARRAY için varyant olarak `[in] SAFEARRAY (VARIANT)* ContextParams`arabirime geçirilen bağlam parametreleri, .

     Bağlam parametreleri, başlatılan sihirbaz türüne ve projenin geçerli durumuna özgü bir dizi değer içerir. IDE bağlam parametrelerini sihirbaza geçirir. Daha fazla bilgi için [Bağlam Parametreleri'ne](../../extensibility/internals/context-parameters.md)bakın.

- Kod segmentinde gösterildiği gibi SAFEARRAY için bir varyant `[in] SAFEARRAY (VARIANT)* CustomParams`olarak arabirime geçirilen özel parametreler, .

     Özel parametreler, kullanıcı tarafından tanımlanan bir dizi parametre içerir. Bir .vsz dosyası özel parametreleri IDE'ye geçirir. Değerler `Param=` deyimler tarafından belirlenir. Daha fazla bilgi için [Özel Parametreler'e](../../extensibility/internals/custom-parameters.md)bakın.

- Arabirimin iade değerleri

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>Ayrıca bkz.
- [Bağlam Parametreleri](../../extensibility/internals/context-parameters.md)
- [Özel Parametreler](../../extensibility/internals/custom-parameters.md)
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
