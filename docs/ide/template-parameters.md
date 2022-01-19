---
title: Project ve öğe şablonu parametreleri
description: Şablon örneği oluşturulurken şablonlarınızın değerlerini değiştirmek için şablon parametrelerini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: fdfc214b88604562d450026aa577765035d59182
ms.sourcegitcommit: ec474f32358861e1f62e92d8262051162f291edc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "136924105"
---
# <a name="template-parameters"></a>Şablon parametreleri

Şablon örneği oluşturulurken şabloninizdeki değerleri değiştirebilirsiniz. Bu işlevi ayarlamak için *şablon parametreleri* kullanın. Şablon parametreleri, şablondaki sınıf adları ve ad alanları gibi değerleri değiştirmek için kullanılabilir. Bir Kullanıcı yeni bir öğe eklediğinde veya proje bu parametrelerin yerini aldığı zaman arka planda çalışan Şablon Sihirbazı.

## <a name="declare-and-enable-template-parameters"></a>Şablon parametrelerini bildir ve Etkinleştir

Şablon parametreleri $*Parameter*$ biçiminde bildirilmiştir. Örneğin:

- $safeprojectname $

- $guid $1

- $guid $5

### <a name="enable-parameter-substitution-in-templates"></a>Şablonlarda parametre değişimini etkinleştir

1. Şablonun *. vstemplate* dosyasında, `ProjectItem` parametre değişimini etkinleştirmek istediğiniz öğeye karşılık gelen öğeyi bulun.

1. `ReplaceParameters` `ProjectItem` Öğesinin özniteliğini olarak ayarlayın `true` .

1. Proje öğesi için kod dosyasında uygun yerlerde parametreler ekleyin. Örneğin, aşağıdaki parametre bir dosyadaki ad alanı için güvenli proje adının kullanıldığını belirtir:

   ```csharp
   namespace $safeprojectname$
   ```

## <a name="reserved-template-parameters"></a>Ayrılmış şablon parametreleri

Aşağıdaki tabloda, herhangi bir şablon tarafından kullanılabilecek ayrılmış şablon parametreleri listelenmektedir:

|Parametre|Açıklama|
|---------------|-----------------|
|ClrVersion|Ortak dil çalışma zamanının (CLR) geçerli sürümü.|
|ext_\*|`ext_`Üst şablonun değişkenlerine başvurmak için herhangi bir parametreye öneki ekleyin. Örneğin, `ext_safeprojectname`.|
|GUID [1-10]|Proje dosyasındaki proje GUID 'INI değiştirmek için kullanılan GUID. En fazla 10 benzersiz GUID belirtebilirsiniz (örneğin, `guid1` ).|
|ItemName|Parametrenin kullanıldığı dosyanın adı.|
|adý|Geçerli bilgisayar adı (örneğin, COMPUTER01).|
|ProjectName|Proje oluşturulduğunda Kullanıcı tarafından girilen ad.|
|RegisteredOrganization|hklm\software\microsoft\ Windows NT \CurrentVersion\RegisteredOrganization. kayıt defteri anahtarı değeri|
|RootNamespace|Geçerli projenin kök ad alanı ve ardından, eğik çizgi ile değiştirilmeleri ile geçerli öğenin alt klasörü gelir. Bu parametre yalnızca öğe şablonları için geçerlidir.|
|safeitemname|Bununla aynı `itemname` ancak tüm güvenli olmayan karakterler ve boşluklar alt çizgi karakterleriyle değiştirilirler.|
|safeitemrootname|Aynı `safeitemname` .|
|safeprojectname|Proje oluşturulduğunda Kullanıcı tarafından belirtilen ad ve tüm güvenli olmayan karakterler ve boşluklar kaldırıldı.|
|time|Geçerli saat, GG/AA/YYYY 00:00:00 biçiminde.|
|belirtilmedisolutionname|Çözümün adı. "Çözüm dizini oluştur" işaretlendiğinde, `specifiedsolutionname` çözüm adı vardır. "Çözüm dizini oluştur" işaretli olmadığında, `specifiedsolutionname` boştur.|
|USERDOMAIN|Geçerli Kullanıcı etki alanı.|
|username|Geçerli Kullanıcı adı.|
|Web ad alanı|Geçerli Web sitesinin adı. Bu parametre, benzersiz sınıf adlarını güvence altına almak için Web formu şablonunda kullanılır. Web sitesi Web sunucusunun kök dizininde ise, bu şablon parametresi Web sunucusunun kök dizinine çözümlenir.|
|yıl|YYYY biçiminde geçerli yıl.|

> [!NOTE]
> Şablon parametreleri büyük/küçük harfe duyarlıdır.

## <a name="custom-template-parameters"></a>Özel şablon parametreleri

Parametre değiştirme sırasında kullanılan varsayılan ayrılmış şablon parametrelerine ek olarak kendi şablon parametrelerinizi ve değerlerini belirtebilirsiniz. daha fazla bilgi için bkz. [customparameters öğesi (Visual Studio şablonları)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-use-the-project-name-for-a-file-name"></a>Örnek: bir dosya adı için proje adını kullanın

Öznitelik içinde bir parametre kullanarak proje öğeleri için değişken dosya adları belirtebilirsiniz `TargetFileName` .

Aşağıdaki örnek, yürütülebilir bir dosyanın adının tarafından belirtilen proje adını kullandığını belirtir `$projectname$` .

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

C# sınıf dosyasındaki ad alanı için güvenli proje adını kullanmak için aşağıdaki sözdizimini kullanın:

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

Proje şablonu için *. vstemplate* dosyasında, `ReplaceParameters="true"` dosyasına başvuruldığınızda özniteliği ekleyin:

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
