---
title: 'Nasıl yapılır: proje şablonları oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- Visual Studio templates, creating project templates
- project templates, metadata files
- Visual Studio templates, project templates
- project templates, custom template locations
- project templates, creating
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f358d5b95349fe99b2a2e01df5158d2c0aa10a11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668045"
---
# <a name="how-to-create-project-templates"></a>Nasıl Yapılır: Proje Şablonları Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu yordam, şablonunuzu bir. zip dosyasında paketleyen şablonu **dışarı aktarma** Sihirbazı 'nı kullanarak bir şablon oluşturmanıza olanak sağlar. Ayrıca, şablonu dışarı aktarma Sihirbazı uzantısını veya [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] dahil olan şablonları kullanarak geliştirilmiş dağıtım için VSıX dosya biçiminde şablonlar oluşturabilirsiniz veya el ile şablon oluşturabilirsiniz.

### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>Standart şablonu dışarı aktarma sihirbazıyla özel bir proje şablonu oluşturmak için

1. Bir proje oluşturun.

    > [!NOTE]
    > Bir şablon için kaynak olacak bir proje adlandırırken yalnızca geçerli tanımlayıcı karakterler kullanın. Geçersiz karakterlerle adlı bir projeden aktarılmış bir şablon, gelecekteki projelerde Şablon temelinde derleme hatalarına neden olabilir. Geçerli tanımlayıcı karakterleri hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları](https://msdn.microsoft.com/library/09d8843b-c0dc-4afe-9dab-87c439a69e66).

2. Proje, bir şablon olarak verilmeye hazırlanana kadar projeyi düzenleyin.

3. Uygun şekilde, parametre değiştirmenin nerede olması gerektiğini belirtmek için kod dosyalarını düzenleyin. Parametre değiştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: şablonda parametreleri değiştirme](../ide/how-to-substitute-parameters-in-a-template.md).

4. **Dosya** menüsünde, **şablonu dışarı aktar**' a tıklayın. **Şablonu dışarı aktarma** Sihirbazı açılır.

5. **Proje şablonu**' na tıklayın.

6. Geçerli çözümünüzde birden fazla projeniz varsa, bir şablona vermek istediğiniz projeleri seçin.

7. **İleri**'ye tıklayın.

8. Şablonunuz için bir simge ve önizleme görüntüsü seçin. Bu, **Yeni proje** iletişim kutusunda görünür.

9. Bir şablon adı ve açıklama girin.

10. **Son**'a tıklayın. Projeniz bir. zip dosyasına aktarılır ve belirtilen çıkış konumuna yerleştirilir ve seçilirse [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] içine aktarılır.

     @No__t_0 yüklüyse, **VSIX proje** şablonunu kullanarak dağıtım için tamamlanmış şablonu bir. vsix dosyasına sardırabilirsiniz. Daha fazla bilgi için bkz. [VSIX proje şablonu Ile çalışmaya](../extensibility/getting-started-with-the-vsix-project-template.md)başlama.

## <a name="see-also"></a>Ayrıca Bkz.
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md) [nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)
