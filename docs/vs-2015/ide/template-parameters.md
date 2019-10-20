---
title: Şablon parametreleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
ms.assetid: 1b567143-08c6-4d7a-b484-49f0671754fe
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d7bb7e0f3dfee3dd1bf3e9b42afd5837a29f6ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646815"
---
# <a name="template-parameters"></a>Şablon Parametreleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Şablonlarınızın parametrelerini kullanarak, şablon örneği oluşturulurken sınıf adları ve ad alanları gibi şablon anahtar bölümlerinin değerlerini değiştirebilirsiniz. Bu parametreler, Kullanıcı **Yeni proje** veya **Yeni öğe Ekle** iletişim kutularında **Tamam** ' a tıkladığında arka planda çalışan Şablon Sihirbazı ile değiştirilmiştir.

## <a name="declaring-and-enabling-template-parameters"></a>Şablon parametrelerini bildirme ve etkinleştirme
 Şablon parametreleri $*Parameter*$ biçiminde bildirilmiştir. Örneğin:

- $safeprojectname $

- $guid $1

- $guid $5

#### <a name="to-enable-parameter-substitution-in-templates"></a>Şablonlarda parametre değişimini etkinleştirmek için

1. Şablonun. vstemplate dosyasında, parametre değişimini etkinleştirmek istediğiniz öğeye karşılık gelen `ProjectItem` öğesini bulun.

2. @No__t_1 öğesinin `ReplaceParameters` özniteliğini `true` olarak ayarlayın.

3. Proje öğesi için kod dosyasında uygun yerlerde parametreler ekleyin. Örneğin, aşağıdaki parametre bir dosyadaki ad alanı için güvenli proje adının kullanılacağını belirtir:

    ```
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Ayrılmış şablon parametreleri
 Aşağıdaki tabloda, herhangi bir şablon tarafından kullanılabilecek ayrılmış şablon parametreleri listelenmektedir.

> [!NOTE]
> Şablon parametreleri büyük/küçük harfe duyarlıdır.

|Parametre|Açıklama|
|---------------|-----------------|
|`clrversion`|Ortak dil çalışma zamanının (CLR) geçerli sürümü.|
|`GUID [1-10]`|Proje dosyasındaki proje GUID 'INI değiştirmek için kullanılan GUID. En fazla 10 benzersiz GUID belirtebilirsiniz (örneğin, `guid1)`.|
|`itemname`|**Yeni öğe Ekle** iletişim kutusunda Kullanıcı tarafından girilen ad.|
|`machinename`|Geçerli bilgisayar adı (örneğin, COMPUTER01).|
|`projectname`|**Yeni proje** iletişim kutusunda Kullanıcı tarafından girilen ad.|
|`registeredorganization`|HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization. 'dan kayıt defteri anahtarı değeri|
|`rootnamespace`|Geçerli projenin kök ad alanı. Bu parametre yalnızca öğe şablonları için geçerlidir.|
|`safeitemname`|**Yeni öğe Ekle** iletişim kutusunda, tüm güvenli olmayan karakterler ve boşluklar kaldırılmış şekilde Kullanıcı tarafından girilen ad.|
|`safeprojectname`|**Yeni proje** iletişim kutusunda, tüm güvenli olmayan karakterler ve boşluklar kaldırılmış şekilde Kullanıcı tarafından belirtilen ad.|
|`time`|Geçerli saat, GG/AA/YYYY 00:00:00 biçiminde.|
|`SpecificSolutionName`|Çözümün adı. "Çözüm dizini oluştur" işaretlendiğinde `SpecificSolutionName` çözüm adı vardır. "Çözüm dizini oluştur" işaretli olmadığında `SpecificSolutionName` boştur.|
|`userdomain`|Geçerli Kullanıcı etki alanı.|
|`username`|Geçerli Kullanıcı adı.|
|`webnamespace`|Geçerli Web sitesinin adı. Bu parametre, benzersiz sınıf adlarını güvence altına almak için Web formu şablonunda kullanılır. Web sitesi Web sunucusunun kök dizinde ise, bu şablon parametresi Web sunucusunun kök dizinine çözümlenir.|
|`year`|YYYY biçiminde geçerli yıl.|

## <a name="custom-template-parameters"></a>Özel şablon parametreleri
 Parametre değiştirme sırasında kullanılan varsayılan ayrılmış şablon parametrelerine ek olarak kendi şablon parametrelerinizi ve değerlerini belirtebilirsiniz. Daha fazla bilgi için bkz. [CustomParameters öğesi (Visual Studio şablonları)](../extensibility/customparameters-element-visual-studio-templates.md)

## <a name="example-replacing-files-names"></a>Örnek: dosya adlarını değiştirme
 @No__t_0 özniteliğiyle bir parametre kullanarak proje öğeleri için değişken dosya adları belirtebilirsiniz. Örneğin,. exe dosyasının, dosya adı olarak `$projectname$` tarafından belirtilen proje adını kullanmasını belirtebilirsiniz.

```
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-using-the-project-name-for-the-namespace-name"></a>Örnek: ad alanı adı için proje adını kullanma
 Class1.cs bir görsel C# sınıf dosyasındaki ad alanı için proje adını kullanmak için, aşağıdaki sözdizimini kullanın:

```
#region Using directives

using System;
using System.Collections.Generic;
using System.Text;

#endregion

namespace $safeprojectname$
{
    public class Class1
        {
            public Class1()
                {

                }
         }
}
```

 Proje şablonu için. vstemplate dosyasında, Class1.cs dosyasına başvurduğunuzda aşağıdaki XML 'yi dahil edin:

```
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Şablonları Özelleştirme](../ide/customizing-project-and-item-templates.md)
