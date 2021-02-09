---
title: GenerateBootstrapper görevi | Microsoft Docs
description: Bir uygulamayı ve önkoşullarını tespit etmek, indirmek ve yüklemek için otomatik bir yol için MSBuild GenerateBootstrapper görevini kullanın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 93dbe9d3bf49118328cb53dcd6602bb5fda77b13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914867"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper görevi

Bir uygulamayı ve önkoşullarını tespit etmek, indirmek ve yüklemek için otomatikleştirilmiş bir yol sağlar. Bir uygulamayı oluşturan tüm bileşenlerin ayrı yükleyicilerini tümleştiren tek bir yükleyici olarak görev yapar.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıda, görevin parametreleri açıklanır `GenerateBootstrapper` .

- `ApplicationFile`

   İsteğe bağlı `String` parametre.

   Tüm Önkoşullar yüklendikten sonra önyükleyicinin uygulamayı yüklemeye başlamak için kullanacağı dosyayı belirtir. Bir yapı hatası, `BootstrapperItems` ne ne de `ApplicationFile` parametresi belirtilmemişse ortaya kalır.

- `ApplicationName`

   İsteğe bağlı `String` parametre.

   Önyükleyici tarafından yüklenecek uygulamanın adını belirtir. Bu ad, önyükleyicinin yükleme sırasında kullandığı kullanıcı arabiriminde görüntülenir.

- `ApplicationRequiresElevation`

   İsteğe bağlı `Boolean` parametre.

   İse `true` , bileşen hedef bilgisayara yüklendiğinde yükseltilmiş izinlerle çalışır.

- `ApplicationUrl`

   İsteğe bağlı `String` parametre.

   Uygulamanın yükleyicisini barındıran Web konumunu belirtir.

- `BootstrapperComponentFiles`

   İsteğe bağlı `String[]` çıkış parametresi.

   Önyükleyici paket dosyalarının oluşturulan konumunu belirtir.

- `BootstrapperItems`

   İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.

   Önyükleyici içine derlenecek ürünleri belirtir. Bu parametreye geçirilen öğelerin aşağıdaki sözdizimi olmalıdır:

  ```xml
  <BootstrapperItem
      Include="ProductCode">
      <ProductName>
          ProductName
      </ProductName>
  </BootstrapperItem>
  ```

   `Include`Öznitelik, yüklenmesi gereken bir önkoşul adını temsil eder. `ProductName`Öğe meta verileri isteğe bağlıdır ve paket bulunamazsa, derleme altyapısı tarafından Kullanıcı dostu bir ad olarak kullanılır. Bu öğeler, hiçbir değer belirtilmediği takdirde, gerekli MSBuild giriş parametreleri değildir `ApplicationFile` . Uygulamanız için yüklenmesi gereken her önkoşul için bir öğe eklemelisiniz.

   Bir yapı hatası, `BootstrapperItems` ne ne de `ApplicationFile` parametresi belirtilmemişse ortaya kalır.

- `BootstrapperKeyFile`

   İsteğe bağlı `String` çıkış parametresi.

   *setup.exe* oluşturulan konumunu belirtir

- `ComponentsLocation`

   İsteğe bağlı `String` parametre.

   Önyükleyici için yüklenecek yükleme önkoşullarını aramak için bir konum belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:

  - `HomeSite`: Önkoşulun bileşen satıcısı tarafından barındırıldığını gösterir.

  - `Relative`: Önkoşulun uygulamanın aynı konumda olduğunu gösterir.

  - `Absolute`: Tüm bileşenlerin merkezi bir URL 'de bulunduğunu belirtir. Bu değer, `ComponentsUrl` giriş parametresiyle birlikte kullanılmalıdır.

    `ComponentsLocation`Belirtilmemişse, `HomeSite` Varsayılan olarak kullanılır.

- `ComponentsUrl`

   İsteğe bağlı `String` parametre.

   Yükleme önkoşullarını içeren URL 'YI belirtir.

- `CopyComponents`

   İsteğe bağlı `Boolean` parametre.

   `true`Önyükleyici, tüm çıktı dosyalarını parametresinde belirtilen yola kopyalar `OutputPath` . `BootstrapperComponentFiles`Parametresinin değerlerinin tümü bu yolu temel almalıdır. `false`, Dosyalar kopyalanmaz ve `BootstrapperComponentFiles` değerler parametre değerini temel alır `Path` .  Bu parametrenin varsayılan değeri `true` .

- `Culture`

   İsteğe bağlı `String` parametre.

   Önyükleyici Kullanıcı arabirimi ve yükleme önkoşulları için kullanılacak kültürü belirtir. Belirtilen kültür kullanılamıyorsa, görev parametresinin değerini kullanır `FallbackCulture` .

- `FallbackCulture`

   İsteğe bağlı `String` parametre.

   Önyükleyici Kullanıcı arabirimi ve yükleme önkoşulları için kullanılacak ikincil kültürü belirtir.

- `OutputPath`

   İsteğe bağlı `String` parametre.

   *setup.exe* ve tüm paket dosyalarının kopyalanacağı konumu belirtir.

- `Path`

   İsteğe bağlı `String` parametre.

   Kullanılabilir tüm önkoşul paketlerinin konumunu belirtir.

- `SupportUrl`

   İsteğe bağlı `String` parametre.

   Önyükleyici yüklemesi başarısız olursa, sağlanacak URL 'YI belirtir.

- `Validate`

   İsteğe bağlı `Boolean` parametre.

   `true`Önyükleyici, belirtilen giriş önyükleyici ÖĞELERINDE XSD doğrulaması gerçekleştirir. Bu parametrenin varsayılan değeri `false` .

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `GenerateBootstrapper` önkoşul olarak .NET Framework 2,0 yüklü olması gereken bir uygulamayı yüklemek için görevini kullanır.

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
