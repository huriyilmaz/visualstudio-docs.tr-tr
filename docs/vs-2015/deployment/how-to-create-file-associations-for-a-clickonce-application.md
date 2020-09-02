---
title: 'Nasıl yapılır: ClickOnce uygulaması Için dosya Ilişkilendirmeleri oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82ffecdc719dad2f38208de00dc95438b3ff36ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697694"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Nasıl yapılır: ClickOnce Uygulaması için Dosya İlişkilendirmeleri Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamalar bir veya daha fazla dosya adı uzantısıyla ilişkilendirilebilen için, Kullanıcı bu türden bir dosya açtığında uygulamanın otomatik olarak başlatılması gerekir. Bir uygulamaya dosya adı uzantısı desteği eklemek [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] basittir.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>ClickOnce uygulaması için dosya ilişkilendirmeleri oluşturmak için  
  
1. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Normal olarak bir uygulama oluşturun veya mevcut uygulamanızı kullanın [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
2. Uygulama bildirimini Not Defteri gibi bir metin veya XML düzenleyicisiyle açın.  
  
3. Öğesini bulun `assembly` . Daha fazla bilgi için bkz. [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md).  
  
4. Öğesinin bir alt öğesi olarak `assembly` bir `fileAssociation` öğesi ekleyin. `fileAssociation`Öğesi dört özniteliğe sahiptir:  
  
   - `extension`: Uygulamayla ilişkilendirmek istediğiniz dosya adı uzantısı.  
  
   - `description`: Windows kabuğu 'nda görünecek dosya türünün açıklaması.  
  
   - `progid`: Kayıt defterinde işaretlemek için dosya türünü benzersiz bir şekilde tanımlayan bir dize.  
  
   - `defaultIcon`: Bu dosya türü için kullanılacak bir simge. Simgenin uygulama bildiriminde bir dosya kaynağı olarak eklenmesi gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulamasına veri dosyası ekleme](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Ve öğelerinin bir örneği için `file` `fileAssociation` bkz. [ \<fileAssociation> öğesi](../deployment/fileassociation-element-clickonce-application.md).  
  
5. Birden çok dosya türünü uygulamayla ilişkilendirmek istiyorsanız, ek `fileAssociation` öğeler ekleyin. `progid`Özniteliğin her biri için farklı olması gerektiğini unutmayın.  
  
6. Uygulama bildirimini tamamladıktan sonra, bildirimi yeniden imzalayın. Bunu komut satırından Mage.exe kullanarak yapabilirsiniz.  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    Daha fazla bilgi için bkz. [Mage.exe (bildirim oluşturma ve düzenleme aracı)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<fileAssociation> Dosyalarında](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
