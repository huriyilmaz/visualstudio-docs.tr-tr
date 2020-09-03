---
title: Kod için Otomasyon sağlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e4d47a72adf787f5d560374e1c44743004d25f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203232"
---
# <a name="providing-automation-for-code"></a>Kod için Otomasyon Sağlama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kodunuz için bir otomasyon modeli oluşturmak gerekli değildir. Ortam SDK 'Sı bu işlemi gerçekleştirmek için bir örnek sağlamaz. Kod modellerine ilişkin Öngörüler için, nesnesine bakın <xref:EnvDTE.CodeModel> .  
  
 Bir kod modeli uygulamak için, iç veri yapınız tarafından belirlenen arabirimleri uygulamanız gerekir. Nesneler `IDispatch` sınıfından türetilmelidir.  
  
 Genişletmediğiniz nesneler <xref:EnvDTE.CodeModel> ve <xref:EnvDTE.FileCodeModel> <xref:EnvDTE.Project> nesnesinden kullanılabilir ve aşağıdaki gibi görünür:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 `CodeModel` `FileCodeModel` `Project` Ve nesnelerinizin döndürdüğü nesnede yalnızca veya arabirimini uygulamayı seçebilirsiniz <xref:EnvDTE.ProjectItem> . Bu arabirimden proje sisteminiz için uygun olan tüm işlevleri sağlayın.  
  
 Standart ve arabirimlerde kullanılamayan Yöntemler veya özellikler gibi özellikler eklemek istiyorsanız, `CodeModel` `FileCodeModel` Standart 'dan devralan kendi arabirimini oluşturun. Son kullanıcıların bunu arayacağı bilmesini sağlamak için, bunu proje sisteminizle birlikte belgelediğinizden emin olun. Standart arabirimini döndürürler, ancak Kullanıcı, varsa, `QueryInterface` Bu yöntemi çağırabilir veya varsa arayüzüne çevirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Otomasyon Modeline Genel Bakış](../../extensibility/internals/automation-model-overview.md)
