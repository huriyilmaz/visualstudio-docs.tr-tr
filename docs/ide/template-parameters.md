---
title: Proje ve öğe şablonu parametreleri
ms.date: 01/02/2018
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 445a4fa7847ea5c9a5cb64da09cf54c763e86d16
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647397"
---
# <a name="template-parameters"></a>Şablon parametreleri

Şablon örneği oluşturulurken şabloninizdeki değerleri değiştirebilirsiniz. Bu işlevi ayarlamak için *şablon parametreleri*kullanın. Şablon parametreleri, şablondaki sınıf adları ve ad alanları gibi değerleri değiştirmek için kullanılabilir. Bir Kullanıcı yeni bir öğe eklediğinde veya proje bu parametrelerin yerini aldığı zaman arka planda çalışan Şablon Sihirbazı.

## <a name="declare-and-enable-template-parameters"></a>Şablon parametrelerini bildir ve Etkinleştir

Şablon parametreleri $*Parameter*$ biçiminde bildirilmiştir. Örneğin:

- $safeprojectname $

- $guid $1

- $guid $5

### <a name="enable-parameter-substitution-in-templates"></a>Şablonlarda parametre değişimini etkinleştir

1. Şablonun *. vstemplate* dosyasında, parametre değişimini etkinleştirmek istediğiniz öğeye karşılık gelen `ProjectItem` öğesini bulun.

1. @No__t_1 öğesinin `ReplaceParameters` özniteliğini `true` olarak ayarlayın.

1. Proje öğesi için kod dosyasında uygun yerlerde parametreler ekleyin. Örneğin, aşağıdaki parametre bir dosyadaki ad alanı için güvenli proje adının kullanıldığını belirtir:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Ayrılmış şablon parametreleri

Aşağıdaki tabloda, herhangi bir şablon tarafından kullanılabilecek ayrılmış şablon parametreleri listelenmektedir:

|Parametre|Açıklama|
|---------------|-----------------|
|ClrVersion|Ortak dil çalışma zamanının (CLR) geçerli sürümü.|
|ext_*|Üst şablonun değişkenlerine başvurmak için `ext_` önekini herhangi bir parametreye ekleyin. Örneğin, `ext_safeprojectname`.|
|GUID [1-10]|Proje dosyasındaki proje GUID 'INI değiştirmek için kullanılan GUID. En fazla 10 benzersiz GUID belirtebilirsiniz (örneğin, `guid1`).|
|ItemName|Parametrenin kullanıldığı dosyanın adı.|
|adý|Geçerli bilgisayar adı (örneğin, COMPUTER01).|
|ProjectName|Proje oluşturulduğunda Kullanıcı tarafından girilen ad.|
|RegisteredOrganization|HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization. 'dan kayıt defteri anahtarı değeri|
|RootNamespace|Geçerli projenin kök ad alanı. Bu parametre yalnızca öğe şablonları için geçerlidir.|
|safeitemname|@No__t_0 ile aynıdır, ancak tüm güvenli olmayan karakterler ve boşluklar alt çizgi karakterleriyle değiştirilmiştir.|
|safeitemrootname|@No__t_0 ile aynı.|
|safeprojectname|Proje oluşturulduğunda Kullanıcı tarafından belirtilen ad ve tüm güvenli olmayan karakterler ve boşluklar kaldırıldı.|
|zaman|Geçerli saat, GG/AA/YYYY 00:00:00 biçiminde.|
|Belirtilmedisolutionname|Çözümün adı. "Çözüm dizini oluştur" işaretlendiğinde `specifiedSolutionName` çözüm adı vardır. "Çözüm dizini oluştur" işaretli olmadığında `specifiedSolutionName` boştur.|
|USERDOMAIN|Geçerli Kullanıcı etki alanı.|
|nitelen|Geçerli Kullanıcı adı.|
|Web ad alanı|Geçerli Web sitesinin adı. Bu parametre, benzersiz sınıf adlarını güvence altına almak için Web formu şablonunda kullanılır. Web sitesi Web sunucusunun kök dizininde ise, bu şablon parametresi Web sunucusunun kök dizinine çözümlenir.|
|yıl|YYYY biçiminde geçerli yıl.|

> [!NOTE]
> Şablon parametreleri büyük/küçük harfe duyarlıdır.

## <a name="custom-template-parameters"></a>Özel şablon parametreleri

Parametre değiştirme sırasında kullanılan varsayılan ayrılmış şablon parametrelerine ek olarak kendi şablon parametrelerinizi ve değerlerini belirtebilirsiniz. Daha fazla bilgi için bkz. [CustomParameters öğesi (Visual Studio şablonları)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-use-the-project-name-for-a-file-name"></a>Örnek: bir dosya adı için proje adını kullanın

@No__t_0 özniteliğinde bir parametre kullanarak proje öğeleri için değişken dosya adları belirtebilirsiniz.

Aşağıdaki örnek, bir yürütülebilir dosya adının `$projectname$` tarafından belirtilen proje adını kullandığını belirtir.

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

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>Örnek: ad alanı adı için güvenli proje adını kullanın

Bir C# sınıf dosyasındaki ad alanı için güvenli proje adını kullanmak için aşağıdaki sözdizimini kullanın:

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
