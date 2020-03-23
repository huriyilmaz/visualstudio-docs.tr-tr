---
title: Proje ve madde şablonu parametreleri
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78169371"
---
# <a name="template-parameters"></a>Şablon parametreleri

Şablon anında olduğunda şablonunuzdaki değerleri değiştirebilirsiniz. Bu işlevselliği ayarlamak için *şablon parametrelerini*kullanın. Şablon parametreleri, şablondaki sınıf adları ve ad alanları gibi değerleri değiştirmek için kullanılabilir. Kullanıcı yeni bir öğe veya proje bu parametrelerin yerini aldığında arka planda çalışan şablon sihirbazı.

## <a name="declare-and-enable-template-parameters"></a>Şablon parametrelerini bildirme ve etkinleştirme

Şablon parametreleri $*parametresi*biçiminde beyan edilir. Örnek:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="enable-parameter-substitution-in-templates"></a>Şablonlarda parametre değiştirmesini etkinleştirme

1. Şablonun *.vstemplate* dosyasında, parametre değişimini etkinleştirmek istediğiniz öğeye karşılık gelen `ProjectItem` öğeyi bulun.

1. Öğenin `ReplaceParameters` özniteliğini `ProjectItem` `true`.

1. Proje öğesinin kod dosyasında, uygun olduğu durumlarda parametreler ilerler. Örneğin, aşağıdaki parametre, bir dosyadaki ad alanı için güvenli proje adının kullanıldığını belirtir:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Ayrılmış şablon parametreleri

Aşağıdaki tablo, herhangi bir şablon tarafından kullanılabilecek ayrılmış şablon parametrelerini listeler:

|Parametre|Açıklama|
|---------------|-----------------|
|clrversion|Ortak dil çalışma zamanının (CLR) geçerli sürümü.|
|ext_*|Üst `ext_` şablonun değişkenlerine başvurmak için herhangi bir parametreye öneki ekleyin. Örneğin, `ext_safeprojectname`.|
|yol gösterici[1-10]|Proje dosyasındaki GUID projesini değiştirmek için kullanılan bir GUID. En fazla 10 benzersiz GUID belirtebilirsiniz `guid1`(örneğin, ).|
|ıtemname|Parametrenin kullanıldığı dosyanın adı.|
|Machinename|Geçerli bilgisayar adı (örneğin, Computer01).|
|Projeadı|Proje oluşturulduğunda kullanıcı tarafından sağlanan ad.|
|kayıtlı organizasyon|HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization'ın kayıt defteri anahtar değeri.|
|rootnamespace|Geçerli projenin kök ad alanı. Bu parametre yalnızca madde şablonları için geçerlidir.|
|safeitemname|Aynı `itemname` ama tüm güvenli olmayan karakterler ve boşluklar alt çizer karakterler ile değiştirilir.|
|safeitemrootname|Aynı `safeitemname`şey.|
|safeprojectname|Proje oluşturulduğunda kullanıcı tarafından sağlanan ancak tüm güvenli olmayan karakterler ve boşluklar kaldırılmış olan ad.|
|time|DD/MM/YYYY 00:00:00 biçiminde geçerli saat.|
|belirtilen çözüm adı|Çözümün adı. "çözüm dizini oluşturma" işaretlendiğinde, `specifiedsolutionname` çözüm adı vardır. "çözüm dizini oluşturma" işaretlenmediğinde `specifiedsolutionname` boştur.|
|kullanıcı etki alanı|Geçerli kullanıcı etki alanı.|
|kullanıcı adı|Geçerli kullanıcı adı.|
|webnamespace|Geçerli web sitesinin adı. Bu parametre, benzersiz sınıf adlarını garanti etmek için web formu şablonunda kullanılır. Web sitesi web sunucusunun kök dizinindeyse, bu şablon parametresi web sunucusunun kök dizinine giderilir.|
|yıl|Yyyy biçiminde geçerli yıl.|

> [!NOTE]
> Şablon parametreleri büyük/küçük harf duyarlıdır.

## <a name="custom-template-parameters"></a>Özel şablon parametreleri

Parametre değişimi sırasında kullanılan varsayılan ayrılmış şablon parametrelerine ek olarak kendi şablon parametrelerinizi ve değerlerinizi belirtebilirsiniz. Daha fazla bilgi için [Bkz. CustomParameters öğesi (Visual Studio şablonları)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-use-the-project-name-for-a-file-name"></a>Örnek: Dosya adı için proje adını kullanma

Öznitelikte `TargetFileName` bir parametre kullanarak proje öğeleri için değişken dosya adları belirtebilirsiniz.

Aşağıdaki örnekte, yürütülebilir bir dosyanın adının `$projectname$`proje adını kullandığı belirtilir.

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

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>Örnek: Ad alanı adı için güvenli proje adını kullanma

C# sınıfı dosyasındaki ad alanının güvenli proje adını kullanmak için aşağıdaki sözdizimini kullanın:

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

Proje şablonu için *.vstemplate* dosyasında, dosyaya `ReplaceParameters="true"` başvururken özniteliği ekleyin:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl kullanılır: Şablondaki yedek parametreler](how-to-substitute-parameters-in-a-template.md)
- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Nasıl yapılı: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md)
- [Şablon Şema Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
