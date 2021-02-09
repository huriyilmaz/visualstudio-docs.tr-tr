---
title: 'Nasıl yapılır: SharePoint dağıtım yapılandırmasını düzenleme | Microsoft Docs'
description: SharePoint dağıtım yapılandırması oluşturmayı veya var olan bir dağıtım yapılandırmasını değiştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 59354537f0c1f22534395da1e0ed3db3929a14a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913644"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Nasıl yapılır: SharePoint dağıtım yapılandırmasını düzenleme
  Dağıtım yapılandırması oluşturabilir veya var olan bir dağıtım yapılandırmasını değiştirebilirsiniz. Örneğin, tek bir adım çalıştırabilir veya dağıtım işlemindeki adımların sırasını değiştirebilirsiniz. Yerleşik ve programlı olarak eklenen yapılandırmaların değiştirilemediğinden, dağıtım yapılandırması oluşturmak veya değiştirmek isteyebilirsiniz.

## <a name="create-a-sharepoint-deployment-configuration"></a>SharePoint dağıtım yapılandırması oluşturma

#### <a name="to-create-a-sharepoint-deployment-configuration"></a>SharePoint dağıtım yapılandırması oluşturmak için

1. **Çözüm Gezgini** bir SharePoint projesi seçin ve ardından menü çubuğunda **Proje**, _ProjectName_**Özellikler**' i seçin.

2. **SharePoint** sekmesinde **Yeni** düğmesini seçin.

     **Yeni dağıtım yapılandırması Ekle** iletişim kutusu görüntülenir.

3. **Ad** metin kutusuna dağıtım yapılandırması için bir ad girin.

4. **Kullanılabilir dağıtım adımları** bölmesinde, dağıtım yapılandırmasına eklemek istediğiniz adımları seçin, ( **>** ) düğmesini seçin ve sonra **Tamam** düğmesini seçin.

    > [!NOTE]
    > Dağıtım öncesi bir komut veya dağıtım sonrası komutu yapılandırdıysanız, bu adımlar yalnızca özelleştirilmiş bir dağıtım yapılandırmasına eklediğinizde çalışır.

## <a name="change-the-active-deployment-configuration"></a>Etkin dağıtım yapılandırmasını değiştirme

#### <a name="to-change-the-active-deployment-configuration"></a>Etkin dağıtım yapılandırmasını değiştirmek için

1. **Çözüm Gezgini** bir SharePoint projesi seçin ve ardından menü çubuğunda **Proje**  >  **\<*ProjectName*> özellikleri**' ni seçin.

2. **SharePoint** sekmesini seçin.

3. **Etkin dağıtım yapılandırması** liste kutusunda, kullanmak istediğiniz dağıtım yapılandırmasının adını seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
