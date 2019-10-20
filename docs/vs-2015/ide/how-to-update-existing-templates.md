---
title: 'Nasıl yapılır: mevcut şablonları güncelleştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b56cf11057957b0eb99fc065ed26af10d8adfbd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670581"
---
# <a name="how-to-update-existing-templates"></a>Nasıl Yapılır: Varolan Şablonları Güncelleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir şablon oluşturup dosyaları bir. zip dosyasına sıkıştırdıktan sonra, şablonu değiştirmek isteyebilirsiniz. Bu işlemi, şablondaki dosyaları el ile değiştirerek veya şablonu temel alan bir projeden yeni bir şablonu dışarı aktararak yapabilirsiniz.

## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Mevcut bir şablonu güncelleştirmek için şablonu dışarı aktarma Sihirbazı 'Nı kullanma
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], var olan bir şablonu güncelleştirmek için kullanılabilen bir **şablonu dışarı aktarma** Sihirbazı sağlar.

#### <a name="to-use-export-template-to-update-an-existing-template"></a>Var olan bir şablonu güncelleştirmek için şablonu dışarı aktar 'ı kullanmak için

1. **Dosya** menüsünde **Yeni** ' ye ve ardından **Yeni proje**' ye tıklayın.

2. Güncelleştirmek istediğiniz şablonu seçin, geçici projeniz için bir ad ve konum girin ve **Tamam**' a tıklayın.

3. Projeyi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] değiştirin.

4. **Dosya** menüsünde, **şablonu dışarı aktar**' ı tıklatın ve **şablonu dışarı aktarma** Sihirbazı ' nı kullanarak yeni bir şablon oluşturun.

5. Güncelleştirilmiş şablon bir. zip dosyasına sıkıştırıldıktan sonra eski Template. zip dosyasını silin.

## <a name="manually-updating-an-existing-template"></a>Mevcut bir şablonu el ile güncelleştirme
 Sıkıştırılmış. zip dosyasındaki dosyaları değiştirerek, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dışındaki mevcut bir şablonu güncelleştirebilirsiniz.

#### <a name="to-manually-update-an-existing-template"></a>Mevcut bir şablonu el ile güncelleştirmek için

1. Şablonu içeren. zip dosyasını bulun. Bu dosya varsayılan olarak, *\\ \ver*

2. . Zip dosyasını ayıklayın.

3. Geçerli şablon dosyalarını değiştirin veya silin ya da şablona yeni dosyalar ekleyin.

4. Güncelleştirilmiş davranışı veya yeni dosyaları işlemek için. vstemplate XML dosyasını açın, değiştirin ve kaydedin. . Vstemplate şeması hakkında daha fazla bilgi için bkz. [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md). Kaynak dosyalarda parametreleştiribilecekleri hakkında daha fazla bilgi için bkz. [şablon parametreleri](../ide/template-parameters.md)

5. Şablonunuzda dosyaları seçin, sağ tıklayın, **Gönder ' e**tıklayın ve ardından **Sıkıştırılmış (daraltılmış) klasör**' e tıklayın. Seçtiğiniz dosyalar bir. zip dosyasında sıkıştırılır.

6. Yeni. zip dosyasını eski. zip dosyası ile aynı dizine yerleştirin.

7. Ayıklanan şablon dosyalarını ve eski şablon. zip dosyasını silin.

8. Geliştirici Komut İstemi bir örneğini (yönetici olarak) başlatın (Başlangıç menüsünde, **Visual Studio 2010/Visual Studio Araçları/Geliştirici komut istemi**).

9. Şu komutu çalıştırın: `devenv /installvstemplates`.

## <a name="see-also"></a>Ayrıca Bkz.
 [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md) [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md) [Visual Studio şablon şeması başvuru](../extensibility/visual-studio-template-schema-reference.md) [şablonu parametreleri](../ide/template-parameters.md) [nasıl yapılır: Başlangıç setleri oluşturma](../ide/how-to-create-starter-kits.md)
