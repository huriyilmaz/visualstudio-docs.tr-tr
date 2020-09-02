---
title: 'Nasıl yapılır: şablonda parametreleri değiştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fe49c928ca3de318410eba56afeae6f4329efed3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670657"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Nasıl Yapılır: Şablonda Parametreleri İkame Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir şablonu temel alan bir dosya oluşturulduğunda sınıf adları ve ad alanları gibi şablon parametrelerini değiştirebilirsiniz. Şablon parametrelerinin tüm listesi için bkz. [şablon parametreleri](../ide/template-parameters.md).

## <a name="procedure"></a>Yordam
 Bu şablona dayalı bir proje oluşturulduğunda, bir şablonun dosyalarındaki parametreleri değiştirebilirsiniz. Bu yordamda, şablonla yeni bir proje oluşturulduğunda, bir ad alanının adını güvenli proje adıyla değiştiren bir şablon oluşturma işlemi açıklanmaktadır.

#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Ad alanı adını proje adıyla değiştirecek bir parametre kullanmak için

1. Parametreyi şablondaki bir veya daha fazla kod dosyasına ekleyin. Örneğin:

    ```
    namespace $safeprojectname$
    ```

    > [!NOTE]
    > Şablon parametreleri $*Parameter*$ biçiminde yazılır.

2. Şablonun. vstemplate dosyasında, `ProjectItem` bu dosyayı içeren öğeyi bulun.

3. `ReplaceParameters`Öğesi için özniteliğini ayarlayın `true` `ProjectItem` . Örneğin:

    ```
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Ayrıca Bkz.
 [Proje ve öğe şablonları](../ide/creating-project-and-item-templates.md) [şablon parametreleri](../ide/template-parameters.md) oluşturma [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md) [ProjectItem öğesi (Visual Studio öğe şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)
