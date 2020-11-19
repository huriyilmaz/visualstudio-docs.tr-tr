---
title: MSBuild görevlerini kullanarak SharePoint çözüm paketi oluşturma
description: Bir geliştirme bilgisayarında komut satırı MSBuild görevlerini kullanarak bir SharePoint çözüm paketi (. wsp) oluşturmayı, temizlemeyi ve doğrulamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f2979073414434d2b8f5be9d070b6b505c09ee14
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903734"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Nasıl yapılır: MSBuild görevlerini kullanarak bir SharePoint çözüm paketi oluşturma
  Bir geliştirme bilgisayarında komut satırı MSBuild görevlerini kullanarak bir SharePoint paketi (*. wsp*) oluşturabilir, temizleyebilir ve doğrulayabilirsiniz. Yapı işlemini bir yapı bilgisayarında Team Foundation Server kullanarak otomatik hale getirmek için de bu komutları kullanabilirsiniz.

## <a name="build-a-sharepoint-package"></a>SharePoint paketi oluşturma

#### <a name="to-build-a-sharepoint-package"></a>SharePoint paketi oluşturmak için

1. Windows **Başlat** menüsünde **tüm programlar**  >  **Donatılar**  >  **komut istemi**' ni seçin.

2. SharePoint projenizin bulunduğu dizine geçin.

3. Proje için bir paket oluşturmak üzere aşağıdaki komutu girin. *ProjectFileName* değerini projenin adıyla değiştirin.

    ```cmd
    msbuild /t:Package ProjectFileName
    ```

     Örneğin, ListDefinition1 adlı bir SharePoint projesini paketlemek için aşağıdaki komutlardan birini çalıştırabilirsiniz.

    ```cmd
    msbuild /t:Package ListDefinition1.vbproj
    msbuild /t:Package ListDefinition1.csproj
    ```

## <a name="clean-a-sharepoint-package"></a>SharePoint paketini Temizleme

#### <a name="to-clean-a-sharepoint-package"></a>Bir SharePoint paketini temizlemek için

1. Bir komut istemi penceresi açın.

2. SharePoint projenizin bulunduğu dizine geçin.

3. Projenin paketini temizlemek için aşağıdaki komutu girin. *ProjectFileName* değerini projenin adıyla değiştirin.

    ```cmd
    msbuild /t:CleanPackage ProjectFileName
    ```

     Örneğin, ListDefinition1 adlı bir SharePoint projesini temizlemek için aşağıdaki komutlardan birini çalıştırabilirsiniz.

    ```cmd
    msbuild /t:CleanPackage ListDefinition1.vbproj
    msbuild /t:CleanPackage ListDefinition1.csproj
    ```

## <a name="validate-a-sharepoint-package"></a>SharePoint paketini doğrulama

#### <a name="to-validate-a-sharepoint-package"></a>Bir SharePoint paketini doğrulamak için

1. Bir komut istemi penceresi açın.

2. SharePoint projenizin bulunduğu dizine geçin.

3. Projenin paketini doğrulamak için aşağıdaki komutu girin. *ProjectFileName* değerini projenin adıyla değiştirin.

    ```cmd
    msbuild /t:ValidatePackage ProjectFileName
    ```

     Örneğin, ListDefinition1 adlı bir SharePoint projesini doğrulamak için aşağıdaki komutlardan birini çalıştırabilirsiniz.

    ```cmd
    msbuild /t:ValidatePackage ListDefinition1.vbproj
    msbuild /t:ValidatePackage ListDefinition1.csproj
    ```

## <a name="set-properties-in-a-sharepoint-package"></a>SharePoint paketindeki özellikleri ayarlama

#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Bir SharePoint paketindeki bir özelliği ayarlamak için

1. Bir komut istemi penceresi açın.

2. SharePoint projenizin bulunduğu dizine geçin.

3. Projenin paketindeki bir özelliği ayarlamak için aşağıdaki komutu girin. *PropertyName* 'i ayarlamak istediğiniz özellik ile değiştirin.

    ```cmd
    msbuild /property:PropertyName=Value
    ```

     Örneğin, uyarı düzeyini ayarlamak için aşağıdaki komutu çalıştırabilirsiniz.

    ```cmd
    msbuild /property:WarningLevel = 2
    ```

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint özellikleri oluşturma](../sharepoint/creating-sharepoint-features.md)
- [Nasıl yapılır: bir SharePoint özelliğini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Nasıl yapılır: SharePoint özelliklerine öğe ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
