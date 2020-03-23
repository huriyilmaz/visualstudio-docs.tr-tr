---
title: GenerateBootstrapper Görev | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateBootstrapper
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateBootstrapper task
- GenerateBootstrapper task [MSBuild]
ms.assetid: ca3ba2c6-d2ea-41f2-b7e3-0fc2b0730460
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6da773fdf6cd84819ea0e73083995f60e3c17e2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634090"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper görevi

Bir uygulamayı ve ön koşulları algılamak, indirmek ve yüklemek için otomatik bir yol sağlar. Bir uygulamayı oluşturan tüm bileşenler için ayrı yükleyicileri tümleştiren tek bir yükleyici olarak hizmet vermektedir.

## <a name="task-parameters"></a>Görev parametreleri

Görevin parametrelerini `GenerateBootstrapper` aşağıda açıklayınız.

- `ApplicationFile`

   İsteğe bağlı `String` parametre.

   Tüm ön koşullar yüklendikten sonra, bootstrapper'ın uygulamanın yüklenmesine başlamak için kullanacağı dosyayı belirtir. `ApplicationFile` Parametre `BootstrapperItems` ne de parametre belirtilmemişse, bir yapı hatası ortaya çıkacaktır.

- `ApplicationName`

   İsteğe bağlı `String` parametre.

   Bootstrapper'ın yükleyeceği uygulamanın adını belirtir. Bu ad, bootstrapper yükleme sırasında kullandığı UI görünür.

- `ApplicationRequiresElevation`

   İsteğe bağlı `Boolean` parametre.

   Hedef `true`bilgisayara yüklendiğinde bileşen yüksek izinlerle çalışıyorsa.

- `ApplicationUrl`

   İsteğe bağlı `String` parametre.

   Uygulamanın yükleyicisini barındıran Web konumunu belirtir.

- `BootstrapperComponentFiles`

   İsteğe bağlı `String[]` çıktı parametresi.

   Bootstrapper paket dosyalarının yerleşik konumunu belirtir.

- `BootstrapperItems`

   İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.

   Bootstrapper içine inşa etmek için ürünleri belirtir. Bu parametreye geçirilen öğeleraşağıdaki sözdizimine sahip olmalıdır:

  ```xml
  <BootstrapperItem
      Include="ProductCode">
      <ProductName>
          ProductName
      </ProductName>
  </BootstrapperItem>
  ```

   Öznitelik, `Include` yüklenmesi gereken bir ön koşulun adını temsil eder. Öğe `ProductName` meta verileri isteğe bağlıdır ve paket bulunamıyorsa yapı altyapısı tarafından kullanıcı dostu bir ad olarak kullanılır. Bu öğeler, hiçbir belirtilmedikçe `ApplicationFile` MSBuild giriş parametreleri gerekli değildir. Uygulamanız için yüklenmesi gereken her ön koşul için bir öğe eklemeniz gerekir.

   `ApplicationFile` Parametre `BootstrapperItems` ne de parametre belirtilmemişse, bir yapı hatası ortaya çıkacaktır.

- `BootstrapperKeyFile`

   İsteğe bağlı `String` çıktı parametresi.

   *setup.exe'nin* yerleşik konumunu belirtir

- `ComponentsLocation`

   İsteğe bağlı `String` parametre.

   Bootstrapper yüklemek için kurulum önkoşullar aramak için bir yer belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:

  - `HomeSite`: Ön koşulun bileşen satıcısı tarafından barındırıldığını gösterir.

  - `Relative`: Ön koşulun uygulamanın aynı yerinde olduğunu gösterir.

  - `Absolute`: Tüm bileşenlerin merkezi bir URL'de bulunacağı anlamına geldiğini gösterir. Bu değer giriş parametresi `ComponentsUrl` ile birlikte kullanılmalıdır.

    `ComponentsLocation` Belirtilmemişse, `HomeSite` varsayılan olarak kullanılır.

- `ComponentsUrl`

   İsteğe bağlı `String` parametre.

   Yükleme ön koşulları içeren URL'yi belirtir.

- `CopyComponents`

   İsteğe bağlı `Boolean` parametre.

   Bootstrapper `true`tüm çıktı dosyalarını `OutputPath` parametrede belirtilen yola kopyalarsa. Parametrenin `BootstrapperComponentFiles` değerlerinin tümü bu yola dayanmalıdır. Dosyalar `false`kopyalanmazsa ve `BootstrapperComponentFiles` değerler `Path` parametrenin değerini temel alıyorsa.  Bu parametrenin varsayılan `true`değeri .

- `Culture`

   İsteğe bağlı `String` parametre.

   Bootstrapper UI ve kurulum ön koşulları için kullanılacak kültürü belirtir. Belirtilen kültür kullanılamıyorsa, görev `FallbackCulture` parametrenin değerini kullanır.

- `FallbackCulture`

   İsteğe bağlı `String` parametre.

   Bootstrapper UI ve kurulum ön koşulları için kullanılacak ikincil kültürü belirtir.

- `OutputPath`

   İsteğe bağlı `String` parametre.

   *Setup.exe* ve tüm paket dosyalarını kopyalamak için konumu belirtir.

- `Path`

   İsteğe bağlı `String` parametre.

   Kullanılabilir tüm ön koşul paketlerinin konumunu belirtir.

- `SupportUrl`

   İsteğe bağlı `String` parametre.

   Bootstrapper yüklemesi başarısız olursa sağlamak için URL belirtir.

- `Validate`

   İsteğe bağlı `Boolean` parametre.

   Eğer `true`, bootstrapper belirtilen giriş bootstrapper öğeleri XSD doğrulama gerçekleştirir. Bu parametrenin varsayılan `false`değeri .

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

Aşağıdaki `GenerateBootstrapper` örnekte, .NET Framework 2.0'ı ön koşul olarak yüklenmesi gereken bir uygulama yüklemek için görev kullanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <BootstrapperFile Include="Microsoft.Net.Framework.2.0">
            <ProductName>Microsoft .NET Framework 2.0</ProductName>
        </BootstrapperFile>
    </ItemGroup>

    <Target Name="BuildBootstrapper">
        <GenerateBootstrapper
            ApplicationFile="WindowsApplication1.application"
            ApplicationName="WindowsApplication1"
            ApplicationUrl="http://mycomputer"
            BootstrapperItems="@(BootstrapperFile)"
            OutputPath="C:\output" />
    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
