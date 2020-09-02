---
title: Yalıtılmış Kabuk uygulamalarını dağıtma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0d8a4cab8d30a56e84d1a6869c2c842b982aea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204672"
---
# <a name="distributing-isolated-shell-applications"></a>Yalıtılmış Kabuk Uygulamaları Dağıtma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalıtılmış bir kabuk uygulaması oluşturmak için Visual Studio 'Yu ve Visual Studio SDK 'sını yüklemelisiniz. Uygulamayı diğer Kullanıcı veya müşterilerin makinelerine dağıtmak için yalıtılmış Kabuk için özel bir yeniden dağıtılabilir paket eklemeniz gerekir.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Yalıtılmış Kabuk uygulamalarını dağıtmaya yönelik önkoşullar  
  
|Ad|Açıklama|  
|----------|-----------------|  
|Visual Studio SDK|Uzantıları geliştirmeniz ve test etmeniz gereken SDK [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Visual Studio yalıtılmış Kabuğu örneğinizi oluşturmak için SDK 'Yı da kullanabilirsiniz.<br /><br /> Visual Studio, SDK için bir önkoşuldur.|  
|Yalıtılmış Kabuk yeniden dağıtılabilir Microsoft Visual Studio|Visual Studio yalıtılmış Kabuğu 'nda bir araçlar ortamı oluşturduğunuzda kurulum programınıza dahil ettiğiniz yeniden dağıtılabilir. Yalıtılmış Kabuk yeniden dağıtılabilir paketi .NET Framework 4,5 ' i içerir.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Uygulama için yükleme programı oluşturma  
 Tümleşik veya yalıtılmış Kabuk uygulamanız için özel bir yükleme programı oluşturmanız gerekir. Daha fazla bilgi için bkz. [yalıtılmış Kabuk uygulaması Yükleme](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Uygulamanıza yönelik güncelleştirmelere izin verme  
 Yükleme programınız, uygulamanızın Microsoft güncelleştirmeleri ya da şirketinizin güncelleştirmeleri tarafından güncelleştirileceği olasılığa izin vermelidir. Güncelleştirmeler hakkında daha fazla bilgi için bkz. [yalıtılmış Kabuk uygulamaları Için bakım yönergeleri](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).
