---
title: Görev SharePoint kullanarak bir çözüm MSBuild oluşturma
description: Geliştirme bilgisayarında komut satırı görevleri kullanarak bir SharePoint çözüm paketini (.wsp) derlemeyi, MSBuild temizlemeyi ve doğrulamayı öğrenin.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 781281c6abce5031166b00d9cdde0b175619f79b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135929"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Nasıl MSBuild kullanarak SharePoint Çözüm Paketi oluşturma
  Bir geliştirme bilgisayarında komut satırı SharePoint bir paket (*.wsp)* MSBuild, temiz ve doğrularsınız. Derleme bilgisayarına yükleme kullanarak derleme işlemini otomatikleştirmek için bu Team Foundation Server da kullanabilirsiniz.

## <a name="build-a-sharepoint-package"></a>SharePoint paketi oluşturma

#### <a name="to-build-a-sharepoint-package"></a>Bir SharePoint derlemek için

1. Başlat menüsünde Windows **Programlar** Donatılar **Komut İstemi'ne**  >    >  **tıklayın.**

2. SharePoint projenizin bulunduğu dizine seçin.

3. Proje için bir paket oluşturmak için aşağıdaki komutu girin. *ProjectFileName'i* projenin adıyla değiştirin.

    ```cmd
    msbuild /t:Package ProjectFileName
    ```

     Örneğin, ListDefinition1 adlı bir SharePoint için aşağıdaki komutlardan birini çalıştırabilirsiniz.

    ```cmd
    msbuild /t:Package ListDefinition1.vbproj
    msbuild /t:Package ListDefinition1.csproj
    ```

## <a name="clean-a-sharepoint-package"></a>Bir SharePoint temizleme

#### <a name="to-clean-a-sharepoint-package"></a>Bir paket SharePoint için

1. Bir komut istemi penceresi açın.

2. SharePoint projenizin bulunduğu dizine seçin.

3. Proje için bir paketi temizlemek için aşağıdaki komutu girin. *ProjectFileName'i* projenin adıyla değiştirin.

    ```cmd
    msbuild /t:CleanPackage ProjectFileName
    ```

     Örneğin, ListDefinition1 adlı bir SharePoint projesini temizlemek için aşağıdaki komutlardan birini çalıştırabilirsiniz.

    ```cmd
    msbuild /t:CleanPackage ListDefinition1.vbproj
    msbuild /t:CleanPackage ListDefinition1.csproj
    ```

## <a name="validate-a-sharepoint-package"></a>Bir SharePoint doğrulama

#### <a name="to-validate-a-sharepoint-package"></a>Bir paket SharePoint için

1. Bir komut istemi penceresi açın.

2. SharePoint projenizin bulunduğu dizine seçin.

3. Proje için bir paketi doğrulamak için aşağıdaki komutu girin. *ProjectFileName'i* projenin adıyla değiştirin.

    ```cmd
    msbuild /t:ValidatePackage ProjectFileName
    ```

     Örneğin, ListDefinition1 adlı bir SharePoint doğrulamak için aşağıdaki komutlardan birini çalıştırabilirsiniz.

    ```cmd
    msbuild /t:ValidatePackage ListDefinition1.vbproj
    msbuild /t:ValidatePackage ListDefinition1.csproj
    ```

## <a name="set-properties-in-a-sharepoint-package"></a>Bir SharePoint paketinde özellikleri ayarlama

#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Bir SharePoint paketinde özellik ayarlamak için

1. Bir komut istemi penceresi açın.

2. SharePoint projenizin bulunduğu dizine seçin.

3. Proje için bir pakette özellik ayarlamak için aşağıdaki komutu girin. *PropertyName'i* ayarlamak istediğiniz özellikle değiştirin.

    ```cmd
    msbuild /property:PropertyName=Value
    ```

     Örneğin, uyarı düzeyini ayarlamak için aşağıdaki komutu çalıştırabilirsiniz.

    ```cmd
    msbuild /property:WarningLevel = 2
    ```

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni SharePoint oluşturma](../sharepoint/creating-sharepoint-features.md)
- [Nasıl SharePoint: SharePoint özelleştirme](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Nasıl kullanılır: SharePoint özelliklerine öğe ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
