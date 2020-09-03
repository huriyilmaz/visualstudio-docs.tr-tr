---
title: Sihirbaz arabirimi (IDTWizard) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 78867fa94851e373ae4d47cd82cd1084a941638c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180346"
---
# <a name="wizard-interface-idtwizard"></a>Sihirbaz Arabirimi (IDTWizard)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
 Başlangıç mekanizması her iki **Yeni proje** için benzerdir ve **Yeni öğe sihirbazları ekler**. Her birini başlatmak için, <xref:EnvDTE.IDTWizard> Dteınternal. h içinde tanımlanan arabirimi çağırın. Tek fark, arabirim çağrıldığında arabirime geçirilen bağlam ve özel parametrelerin kümesidir.  
  
 Aşağıdaki bilgiler, <xref:EnvDTE.IDTWizard> sihirbazların IDE 'de çalışmak için uygulaması gereken arabirimi açıklar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . IDE, <xref:EnvDTE.IDTWizard.Execute%2A> sihirbazdaki yöntemi çağırarak, aşağıdakileri geçirerek:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlam parametreleri](../../extensibility/internals/context-parameters.md)   
 [Özel parametreler](../../extensibility/internals/custom-parameters.md)   
 ['Nı](../../extensibility/internals/wizards.md)   
 [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
