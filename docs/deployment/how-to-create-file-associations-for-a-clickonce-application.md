---
title: Dosya ilişkilendirmeleri oluşturma (ClickOnce uygulama)
description: Bir uygulamanın bir ClickOnce veya daha fazla dosya adı uzantısıyla ilişkilendirilebilir, böylece kullanıcı böyle bir dosyayı açtığında uygulama başlatılır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: f05e61bc44f8a2db5f4a498df369131cc728df0a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127967"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Nasıl kurulur: Bir uygulama için dosya ClickOnce oluşturma
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamalar bir veya daha fazla dosya adı uzantısıyla ilişkilendirilebilir, böylece kullanıcı bu tür bir dosyayı açtığında uygulama otomatik olarak başlatılır. Bir uygulamaya dosya adı uzantısı desteği [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eklemek oldukça kolaydır.

### <a name="to-create-file-associations-for-a-clickonce-application"></a>Bir uygulama için dosya ilişkilendirmeleri ClickOnce için

1. Normalde [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir uygulama oluşturun veya mevcut uygulamanızı [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kullanın.

2. Uygulama bildirimini, uygulama bildirimi gibi bir metin veya XML Not Defteri.

3. öğesini `assembly` bulun. Daha fazla bilgi için [bkz. ClickOnce bildirimi.](../deployment/clickonce-application-manifest.md)

4. öğesinin alt `assembly` öğesi olarak bir öğesi `fileAssociation` ekleyin. öğesinin `fileAssociation` dört özniteliği vardır:

   - `extension`: Uygulamayla ilişkilendirmek istediğiniz dosya adı uzantısı.

   - `description`: Dosya türünün, dosya kabuğunda görünecek Windows.

   - `progid`: Kayıt defterinde işaretlemek için dosya türünü benzersiz bir şekilde tanımlayan dize.

   - `defaultIcon`: Bu dosya türü için bir simge. Simge, uygulama bildirimine bir dosya kaynağı olarak eklenmiştir. Daha fazla bilgi için, [bkz. How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

     ve öğeleri örneği için `file` `fileAssociation` bkz. [ \<fileAssociation> Öğesi.](../deployment/fileassociation-element-clickonce-application.md)

5. Uygulamayla birden fazla dosya türünü ilişkilendirmek için ek öğeler `fileAssociation` ekleyin. Özniteliğin `progid` her biri için farklı olması gerektiğini unutmayın.

6. Uygulama bildirimini tamamladikten sonra bildirimi yeniden imzalar. Bunu komut satırına kullanarak komutunu kullanarak *Mage.exe.*

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    Daha fazla bilgi için [bkz.Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="see-also"></a>Ayrıca bkz.
- [\<fileAssociation> Öğe](../deployment/fileassociation-element-clickonce-application.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)