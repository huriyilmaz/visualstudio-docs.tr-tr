---
title: Project ve öğe şablonu parametreleri
description: Şablon örneği değiştirilebilirken şablonun değerlerini değiştirmek için şablon parametrelerini kullanmayı öğrenin.
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
ms.openlocfilehash: bd48e160b4134ff3439a1258386328b27f84b184
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116818"
---
# <a name="template-parameters"></a>Şablon parametreleri

Şablon örneği değiştirilebilir. Bu işlevi ayarlamak için şablon *parametrelerini kullanın.* Şablon parametreleri, şablonda sınıf adları ve ad alanları gibi değerleri değiştirmek için kullanılabilir. Kullanıcı yeni bir öğe veya proje eklenirken arka planda çalışan şablon sihirbazı bu parametrelerin yerini alar.

## <a name="declare-and-enable-template-parameters"></a>Şablon parametrelerini bildir ve etkinleştir

Şablon parametreleri $ parametresi $ biçiminde *bildirildi.* Örnek:

- $safeprojectname$

- $guid 1$

- $guid 5$

### <a name="enable-parameter-substitution-in-templates"></a>Şablonlarda parametre değiştirmeyi etkinleştirme

1. Şablonun *.vstemplate* dosyasında, parametre değiştirmeyi etkinleştirmek `ProjectItem` istediğiniz öğeye karşılık gelen öğeyi bulun.

1. öğesinin `ReplaceParameters` özniteliğini `ProjectItem` olarak `true` ayarlayın.

1. Proje öğesinin kod dosyasına uygun olduğunda parametreleri dahil etmek. Örneğin, aşağıdaki parametre bir dosyada ad alanı için güvenli proje adının kullan olduğunu belirtir:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Ayrılmış şablon parametreleri

Aşağıdaki tabloda herhangi bir şablon tarafından kullanılan ayrılmış şablon parametreleri liste almaktadır:

|Parametre|Açıklama|
|---------------|-----------------|
|clrversion|Ortak dil çalışma zamanının (CLR) geçerli sürümü.|
|ext_*|Üst `ext_` şablonun değişkenlerine başvurmak için ön eki herhangi bir parametreye ekleyin. Örneğin, `ext_safeprojectname`.|
|guid[1-10]|Proje dosyasındaki proje GUID'sini değiştirmek için kullanılan GUID. En fazla 10 benzersiz GUID belirtesiniz (örneğin, `guid1` ).|
|ıtemname|Parametresinin içinde kullanılan dosyanın adı.|
|Machinename|Geçerli bilgisayar adı (örneğin, Bilgisayar01).|
|Projeadı|Proje oluşturulduğunda kullanıcı tarafından sağlanan ad.|
|registeredorganization|HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization'dan kayıt defteri anahtarı değeri.|
|rootnamespace|Geçerli projenin kök ad alanı. Bu parametre yalnızca öğe şablonları için geçerlidir.|
|safeitemname|Ile `itemname` aynıdır, ancak tüm güvenli olmayan karakterler ve boşluklar alt çizgi karakterleriyle değiştirilir.|
|safeitemrootname|ile `safeitemname` aynı.|
|safeprojectname|Proje oluşturulduğunda kullanıcı tarafından sağlanan ancak güvenli olmayan karakterlerin ve boşlukların kaldırıldığı ad.|
|time|Geçerli saat: DD/AA/YYYY 00:00:00.|
|specifiedsolutionname|Çözümün adı. "Çözüm dizini oluştur" işaretli `specifiedsolutionname` olduğunda, çözüm adı vardır. "Çözüm dizini oluştur" işaretli değilken `specifiedsolutionname` boştur.|
|userdomain|Geçerli kullanıcı etki alanı.|
|username|Geçerli kullanıcı adı.|
|webnamespace|Geçerli web sitesinin adı. Bu parametre, benzersiz sınıf adlarını garanti etmek için web formu şablonunda kullanılır. Web sitesi web sunucusunun kök dizininde ise, bu şablon parametresi web sunucusunun kök dizinine çözümler.|
|yıl|YYYY biçimindeki geçerli yıl.|

> [!NOTE]
> Şablon parametreleri büyük/büyük/büyük harfe duyarlıdır.

## <a name="custom-template-parameters"></a>Özel şablon parametreleri

Parametre değiştirme sırasında kullanılan varsayılan ayrılmış şablon parametrelerine ek olarak kendi şablon parametrelerinizi ve değerlerinizi belirtebilirsiniz. Daha fazla bilgi için bkz. [CustomParameters öğesi (Visual Studio şablonları)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-use-the-project-name-for-a-file-name"></a>Örnek: Dosya adı için proje adını kullanın

özniteliğinde bir parametre kullanarak proje öğeleri için değişken dosya adları `TargetFileName` belirtebilirsiniz.

Aşağıdaki örnek, yürütülebilir bir dosyanın adının tarafından belirtilen proje adını kullandığını `$projectname$` belirtir.

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

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>Örnek: Ad alanı adı için güvenli proje adını kullanın

C# sınıf dosyasındaki ad alanı için güvenli proje adını kullanmak üzere aşağıdaki sözdizimini kullanın:

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

Proje *şablonunun .vstemplate* dosyasına, dosyaya `ReplaceParameters="true"` başvurarak özniteliğini dahil olun:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılacaklar: Şablonda parametrelerin yerini ekleme](how-to-substitute-parameters-in-a-template.md)
- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Nasıl: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md)
- [Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
