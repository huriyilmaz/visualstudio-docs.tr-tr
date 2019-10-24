---
title: Sihirbaz arabirimi (IDTWizard) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f571fbd0a68ddbf56b637071ac250159461f61d1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721539"
---
# <a name="wizard-interface-idtwizard"></a>Sihirbaz Arabirimi (IDTWizard)
Tümleşik geliştirme ortamı (IDE) sihirbazları ile iletişim kurmak için <xref:EnvDTE.IDTWizard> arabirimini kullanır. Sihirbazlar IDE 'ye yüklenebilmek için bu arabirimi uygulamalıdır.

 <xref:EnvDTE.IDTWizard.Execute%2A> yöntemi, <xref:EnvDTE.IDTWizard> arabirimiyle ilişkili tek yöntemdir. Sihirbazlar bu yöntemi uygular ve IDE, yöntemi arayüzde çağırır. Aşağıdaki örnek, yönteminin imzasını gösterir.

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

 Başlangıç mekanizması her iki **Yeni proje** için benzerdir ve **Yeni öğe sihirbazları ekler** . Her birini başlatmak için, Dteınternal. h içinde tanımlanan <xref:EnvDTE.IDTWizard> arabirimini çağırın. Tek fark, arabirim çağrıldığında arabirime geçirilen bağlam ve özel parametrelerin kümesidir.

 Aşağıdaki bilgiler, sihirbazların [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 'de çalışmak için uygulaması gereken <xref:EnvDTE.IDTWizard> arabirimini açıklamaktadır. IDE, sihirbazda <xref:EnvDTE.IDTWizard.Execute%2A> yöntemini çağırarak, aşağıdakileri geçirerek:

- DTE nesnesi

     DTE nesnesi otomasyon modelinin köküdür.

- Kod kesiminde gösterildiği gibi pencere iletişim kutusunun tutamacı `hwndOwner ([in] long)`.

     Sihirbaz bu `hwndOwner` sihirbaz iletişim kutusu için üst öğe olarak kullanır.

- Bağlam parametreleri, kod kesiminde gösterildiği gibi SAFEARRAY için değişken olarak geçildi. `[in] SAFEARRAY (VARIANT)* ContextParams`.

     Bağlam parametreleri, başlatılmakta olan sihirbaz türüne ve projenin geçerli durumuna özgü bir değer dizisi içerir. IDE, bağlam parametrelerini sihirbaza geçirir. Daha fazla bilgi için bkz. [Bağlam parametreleri](../../extensibility/internals/context-parameters.md).

- Kod kesiminde gösterildiği gibi, bir SAFEARRAY için bir değişken olarak arabirime geçirilen özel parametreler `[in] SAFEARRAY (VARIANT)* CustomParams`.

     Özel parametreler, Kullanıcı tanımlı parametrelerin dizisini içerir. Bir. vsz dosyası, IDE 'ye özel parametreler geçirir. Değerler `Param=` deyimleri tarafından belirlenir. Daha fazla bilgi için bkz. [özel parametreler](../../extensibility/internals/custom-parameters.md).

- Arabirim için dönüş değerleri

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