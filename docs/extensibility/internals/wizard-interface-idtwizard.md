---
title: Sihirbaz arabirimi (IDTWizard) | Microsoft Docs
description: IDE, sihirbazlarla iletişim kurmak için IDTWizard arabirimini kullanır. Sihirbazlar, IDE 'ye yüklenmek için bu arabirimi uygulamalıdır.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e87759a979d0c680018d99a1e18a12e645f430c6
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487770"
---
# <a name="wizard-interface-idtwizard"></a>Sihirbaz Arabirimi (IDTWizard)
Tümleşik geliştirme ortamı (IDE), <xref:EnvDTE.IDTWizard> sihirbazları ile iletişim kurmak için arabirimini kullanır. Sihirbazlar IDE 'ye yüklenebilmek için bu arabirimi uygulamalıdır.

 <xref:EnvDTE.IDTWizard.Execute%2A>Yöntemi, arabirimiyle ilişkili tek yöntemdir <xref:EnvDTE.IDTWizard> . Sihirbazlar bu yöntemi uygular ve IDE, yöntemi arayüzde çağırır. Aşağıdaki örnek, yönteminin imzasını gösterir.

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

 Başlangıç mekanizması her iki **Yeni proje** için benzerdir ve **Yeni öğe sihirbazları ekler** . Her birini başlatmak için, <xref:EnvDTE.IDTWizard> Dteınternal. h içinde tanımlanan arabirimi çağırın. Tek fark, arabirim çağrıldığında arabirime geçirilen bağlam ve özel parametrelerin kümesidir.

 Aşağıdaki bilgiler, <xref:EnvDTE.IDTWizard> sihirbazların IDE 'de çalışmak için uygulaması gereken arabirimi açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . IDE, <xref:EnvDTE.IDTWizard.Execute%2A> sihirbazdaki yöntemi çağırarak, aşağıdakileri geçirerek:

- DTE nesnesi

     DTE nesnesi otomasyon modelinin köküdür.

- Kod kesiminde gösterildiği gibi pencere iletişim kutusunun tutamacı `hwndOwner ([in] long)` .

     Sihirbaz bunu `hwndOwner` sihirbaz için üst öğe olarak kullanır iletişim kutusu.

- Bağlam parametreleri, kod segmenti gösterildiği gibi bir SAFEARRAY için değişken olarak arabirime geçirilir `[in] SAFEARRAY (VARIANT)* ContextParams` .

     Bağlam parametreleri, başlatılmakta olan sihirbaz türüne ve projenin geçerli durumuna özgü bir değer dizisi içerir. IDE, bağlam parametrelerini sihirbaza geçirir. Daha fazla bilgi için bkz. [Bağlam parametreleri](../../extensibility/internals/context-parameters.md).

- Kod kesiminde gösterildiği gibi, bir SAFEARRAY için bir değişken olarak arabirime geçirilen özel parametreler `[in] SAFEARRAY (VARIANT)* CustomParams` .

     Özel parametreler, Kullanıcı tanımlı parametrelerin dizisini içerir. Bir. vsz dosyası, IDE 'ye özel parametreler geçirir. Değerler `Param=` deyimlerle belirlenir. Daha fazla bilgi için bkz. [özel parametreler](../../extensibility/internals/custom-parameters.md).

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
