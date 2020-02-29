---
title: Proje ve öğe şablon parametreleri
ms.date: 01/02/2018
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 7076e8f5718e44cc382eb0768e6456dbd6ee5664
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78169371"
---
# <a name="template-parameters"></a>Şablon parametreleri

Şablon örneği başlatıldığında, şablonunuzda değerleri değiştirebilirsiniz. Bu işlevi ayarlamak için *şablon parametreleri*kullanın. Şablon parametresi sınıf adları ve şablonda ad alanları gibi değerleri değiştirmek için kullanılabilir. Şablon Sihirbazı, bir kullanıcı yeni bir öğe ekler veya proje bu parametreler, arka planda çalışır.

## <a name="declare-and-enable-template-parameters"></a>Şablon parametrelerini bildir ve Etkinleştir

Şablon parametreleri $*Parameter*$ biçiminde bildirilmiştir. Örneğin:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="enable-parameter-substitution-in-templates"></a>Şablonlarda parametre değişimini etkinleştir

1. Şablonun *. vstemplate* dosyasında, parametre değişimini etkinleştirmek istediğiniz öğeye karşılık gelen `ProjectItem` öğesini bulun.

1. `ProjectItem` öğesinin `ReplaceParameters` özniteliğini `true`olarak ayarlayın.

1. Proje öğesi için kod dosyasında, uygun yerlerde parametreleri içerir. Örneğin, aşağıdaki parametre güvenli proje adı ad alanında bir dosya için kullanıldığını belirtir:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Ayrılmış şablon parametreleri

Aşağıdaki tabloda, herhangi bir şablon tarafından kullanılabilecek ayrılmış şablon parametreleri listelenmektedir:

|Parametre|Açıklama|
|---------------|-----------------|
|clrversion|Geçerli sürümü ortak dil çalışma zamanı (CLR).|
|ext_ *|Üst şablonun değişkenlerine başvurmak için `ext_` önekini herhangi bir parametreye ekleyin. Örneğin, `ext_safeprojectname`.|
|1-10 GUID|' % S'projesi bir proje dosyasında GUID değiştirmek için kullanılan bir GUID. En fazla 10 benzersiz GUID belirtebilirsiniz (örneğin, `guid1`).|
|ItemName|Parametrenin kullanıldığı dosyanın adı.|
|MachineName|Geçerli bilgisayar adı (örneğin, Computer01).|
|ProjectName|Proje oluşturulduğunda Kullanıcı tarafından girilen ad.|
|RegisteredOrganization|Kayıt defteri anahtar değeri HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|RootNamespace|Geçerli projenin kök ad alanı. Bu parametre, yalnızca öğe şablonları için geçerlidir.|
|safeitemname|`itemname` ile aynıdır, ancak tüm güvenli olmayan karakterler ve boşluklar alt çizgi karakterleriyle değiştirilmiştir.|
|safeitemrootname|`safeitemname`ile aynı.|
|safeprojectname|Proje oluşturulduğunda Kullanıcı tarafından belirtilen ad ve tüm güvenli olmayan karakterler ve boşluklar kaldırıldı.|
|time|GG/AA/YYYY biçiminde geçerli saati 00:00:00.|
|belirtilmedisolutionname|Çözüm adı. "Çözüm dizini oluştur" işaretlendiğinde `specifiedsolutionname` çözüm adı vardır. "Çözüm dizini oluştur" işaretli olmadığında `specifiedsolutionname` boştur.|
|USERDOMAIN|Geçerli kullanıcı etki alanı.|
|kullanıcı adı|Geçerli kullanıcı adı.|
|webnamespace|Geçerli Web sitesinin adı. Bu parametre, web formu şablonda benzersiz sınıf isimleri güvence altına almak için kullanılır. Web sitesi web sunucusunun kök dizininde ise, bu şablon parametresi web sunucusunun kök dizinine çözümler.|
|yıl|YYYY biçiminde geçerli yıl.|

> [!NOTE]
> Şablon parametreleri büyük/küçük harfe duyarlıdır.

## <a name="custom-template-parameters"></a>Özel şablon parametreleri

Kendi şablon parametreleri ve değerleri, ek parametre değiştirme sırasında kullanılan ayrılmış varsayılan şablon parametreleri olarak belirtebilirsiniz. Daha fazla bilgi için bkz. [CustomParameters öğesi (Visual Studio şablonları)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-use-the-project-name-for-a-file-name"></a>Örnek: Proje adı için bir dosya adı kullanın.

`TargetFileName` özniteliğinde bir parametre kullanarak proje öğeleri için değişken dosya adları belirtebilirsiniz.

Aşağıdaki örnek, bir yürütülebilir dosya adının `$projectname$`tarafından belirtilen proje adını kullandığını belirtir.

```xml
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>Örnek: ad alanı adı için güvenli bir proje adı kullanın.

C# sınıf dosyasında ad alanı için güvenli bir proje adı kullanmak için aşağıdaki sözdizimini kullanın:

```csharp
namespace $safeprojectname$
{
    public class Class1
    {
        public Class1()
        { }
    }
}
```

Proje şablonu için *. vstemplate* dosyasında, dosyaya başvurduğunuzda `ReplaceParameters="true"` özniteliği ekleyin:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: şablonda parametreleri değiştirme](how-to-substitute-parameters-in-a-template.md)
- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Nasıl yapılır: proje şablonları oluşturma](../ide/how-to-create-project-templates.md)
- [Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
