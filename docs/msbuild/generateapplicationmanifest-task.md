---
title: GenerateApplicationManifest görevi | Microsoft Docs
description: bir ClickOnce uygulama bildirimi veya yerel bildirim sağlamak için MSBuild generateapplicationmanifest görevini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateApplicationManifest task
- HostInBrowser property (MSBuild)
- GenerateApplicationManifest task [MSBuild]
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: a6d84d274fc67fa01c49db315f8a550e23c6bec8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085097"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest görevi

bir ClickOnce uygulama bildirimi veya yerel bildirim oluşturur. Yerel bildirim bileşeni, bileşen için benzersiz bir kimlik tanımlayarak ve bileşeni oluşturan tüm derlemeleri ve dosyaları tanımlayarak bir bileşeni tanımlar. ClickOnce uygulama bildirimi, uygulamanın giriş noktasını belirterek ve uygulama güvenlik düzeyini belirterek yerel bir bildirimi genişletir.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda, görevi için parametreler açıklanmaktadır `GenerateApplicationManifest` .

| Parametre | Açıklama |
|---------------------------------| - |
| `AssemblyName` | İsteğe bağlı `String` parametre.<br /><br /> `Name`Oluşturulan bildirim için derleme kimliği alanını belirtir. Bu parametre belirtilmemişse, ad `EntryPoint` veya `InputManifest` parametrelerinden algılanır. Ad oluşturuoluşturulamadığı takdirde, görev bir hata oluşturur. |
| `AssemblyVersion` | İsteğe bağlı `String` parametre.<br /><br /> `Version`Oluşturulan bildirim için derleme kimliği alanını belirtir. Bu parametre belirtilmemişse, varsayılan "1.0.0.0" değeri kullanılır. |
| `ClrVersion` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın gerektirdiği ortak dil çalışma zamanının (CLR) en düşük sürümünü belirtir. Varsayılan değer, yapı sistemi tarafından kullanılan CLR sürümüdür. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır. |
| `ConfigFile` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Hangi öğenin uygulama yapılandırma dosyasını içerdiğini belirtir. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır. |
| `Dependencies` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Oluşturulan bildirim için bağımlı derlemelerin kümesini tanımlayan bir öğe listesini belirtir. Her öğe, ek dağıtım durumu ve bağımlılık türü belirtmek için öğe meta verileri tarafından daha ayrıntılı bir şekilde açıklanabilir. Daha fazla bilgi için bkz. [öğe meta verileri](#item-metadata). |
| `Description` | İsteğe bağlı `String` parametre.<br /><br /> Uygulama veya bileşen için açıklama belirtir. |
| `EntryPoint` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Oluşturulan bildirim derlemesi için giriş noktasını gösteren tek bir öğeyi belirtir.<br /><br /> ClickOnce uygulama bildirimi için, bu parametre uygulama çalıştırıldığında başlayan derlemeyi belirtir. |
| `ErrorReportUrl` | İsteğe bağlı <xref:System.String?displayProperty=fullName> parametre.<br /><br /> ClickOnce yüklemelerinde hata raporları sırasında iletişim kutularında görüntülenen web sayfasının URL 'sini belirtir. |
| `FileAssociations` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> ClickOnce dağıtım bildirimiyle ilişkili bir veya daha fazla dosya türünün listesini belirtir.<br /><br /> dosya ilişkilendirmeleri yalnızca .NET Framework 3,5 veya üzeri hedeflenirse geçerlidir. |
| `Files` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bildirime dahil edilecek dosyalar. Her dosyanın tam yolunu belirtin. |
| `HostInBrowser` | İsteğe bağlı <xref:System.Boolean> parametre.<br /><br /> Varsa `true` , uygulama bir tarayıcıda barındırılır (WPF Web tarayıcısı uygulamaları gibi). |
| `IconFile` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Uygulama simge dosyasını gösterir. Uygulama simgesi oluşturulan uygulama bildiriminde ifade edilir ve **Başlat menüsü** ve **Program Ekle/Kaldır** iletişim kutusu için kullanılır. Bu giriş belirtilmemişse, varsayılan bir simge kullanılır. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır. |
| `InputManifest` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Bildirim Oluşturucu için temel olarak hizmet veren bir giriş XML belgesi gösterir. Bu, uygulama güvenliği veya özel bildirim tanımları gibi yapılandırılmış verilerin çıktı bildiriminde yansıtılmasına olanak tanır. XML belgesindeki kök öğesi asmv1 ad alanında bir derleme düğümü olmalıdır. |
| `IsolatedComReferences` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Oluşturulan bildirimde yalıtmak için COM bileşenlerini belirtir. Bu parametre, "kayıt ücretsiz COM" dağıtımı için COM bileşenlerini yalıtma yeteneğini destekler. Standart COM kayıt tanımlarına sahip bir bildirimi otomatik olarak oluşturarak işe yarar. Ancak, bunun düzgün çalışması için COM bileşenlerinin derleme makinesinde kayıtlı olması gerekir. |
| `ManifestType` | İsteğe bağlı `String` parametre.<br /><br /> Oluşturulacak bildirim türünü belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Bu parametre belirtilmezse, görev varsayılan olarak olur `ClickOnce` . |
| `MaxTargetPath` | İsteğe bağlı `String` parametre.<br /><br /> ClickOnce uygulama dağıtımında bir dosya yolunun izin verilen en fazla uzunluğunu belirtir. Bu değer belirtilmişse, uygulamadaki her dosya yolunun uzunluğu bu sınıra karşı denetlenir. Sınırı aşan öğeler bir yapı uyarısında oluşturulur. Bu giriş belirtilmezse veya sıfırsa hiçbir denetim yapılmaz. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır. |
| `OSVersion` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın gerektirdiği en düşük işletim sistemi (OS) sürümünü belirtir. örneğin, "5.1.2600.0" değeri işletim sisteminin Windows XP olduğunu gösterir. bu parametre belirtilmemişse, .NET Framework desteklenen en düşük işletim sistemi olan Windows 98 ikinci sürümü gösteren "4.10.0.0" değeri kullanılır. Görev yerel bir bildirim oluşturuyorsa bu giriş yok sayılır. |
| `OutputManifest` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> Oluşturulan çıkış bildirimi dosyasının adını belirtir. Bu parametre belirtilmemişse, çıkış dosyasının adı oluşturulan bildirimin kimliğinden algılanır. |
| `Platform` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın hedef platformunu belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Bu parametre belirtilmezse, görev varsayılan olarak olur `AnyCPU` . |
| `Product` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın adını belirtir. Bu parametre belirtilmemişse, ad oluşturulan bildirimin kimliğinden algılanır. Bu ad, **Başlangıç** menüsündeki kısayol adı için kullanılır ve **Program Ekle veya Kaldır** iletişim kutusunda görünen adın bir parçasıdır. |
| `Publisher` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın yayımcısını belirtir. Bu parametre belirtilmemişse, ad kayıtlı kullanıcıdan veya oluşturulan bildirimin kimliğiyle algılanır. Bu ad, **Başlangıç** menüsündeki klasör adı için kullanılır ve **Program Ekle veya Kaldır** iletişim kutusunda görünen adın bir parçasıdır. |
| `RequiresMinimumFramework35SP1` | İsteğe bağlı `Boolean` parametre.<br /><br /> doğru ise, uygulama .NET Framework 3,5 SP1 veya daha yeni bir sürümü gerektirir. |
| `TargetCulture` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın kültürünü tanımlar ve `Language` oluşturulan bildirim için derleme kimliği alanını belirtir. Bu parametre belirtilmezse, uygulamanın kültür sabiti olduğu varsayılır. |
| `TargetFrameworkMoniker` | İsteğe bağlı `String` parametre.<br /><br /> Hedef çerçevenin bilinen adını belirtir. |
| `TargetFrameworkProfile` | İsteğe bağlı `String` parametre.<br /><br /> Hedef çerçeve profilini belirtir. |
| `TargetFrameworkSubset` | İsteğe bağlı `String` parametre.<br /><br /> hedeflenecek .NET Framework alt kümesinin adını belirtir. |
| `TargetFrameworkVersion` | İsteğe bağlı `String` parametre.<br /><br /> projenin hedef .NET Framework belirtir. |
| `TrustInfoFile` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> Uygulama güvenliğini belirten bir XML belgesini gösterir. XML belgedeki kök öğe asmv2 ad alanı içinde bir trustInfo düğümü olmalıdır. Görev yerel bir bildirim üretiyorsa, bu parametre yoksayılır. |
| `UseApplicationTrust` | İsteğe `Boolean` bağlı parametre.<br /><br /> True `Product` ise, `Publisher` , ve `SupportUrl` özellikleri uygulama bildirimine yazılır. |

## <a name="remarks"></a>Açıklamalar

Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.GenerateManifestBase> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Görev sınıfının parametrelerinin listesi için bkz. [Görev temel sınıfı.](../msbuild/task-base-class.md)

Görevi kullanma hakkında bilgi için `GenerateDeploymentManifest` bkz. [GenerateApplicationManifest görevi.](../msbuild/generateapplicationmanifest-task.md)

Bağımlılıklar ve dosyalar için girişler, her öğe için ek dağıtım durumu belirtmek için öğe meta verileriyle daha fazla dekore edilmiş olabilir.

## <a name="item-metadata"></a>Öğe meta verileri

|Meta veri adı|Açıklama|
|-------------------|-----------------|
|`DependencyType`|Bağımlılığın yayım olup olmadığını ve uygulamayla mı yoksa önkoşulla mı yük olduğunu gösterir. Bu meta veriler tüm bağımlılıklar için geçerlidir, ancak dosyalar için kullanılamaz. Bu meta veriler için kullanılabilir değerler:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Yükleme varsayılan değerdir.|
|`AssemblyType`|Bağımlılığın yönetilen bir derleme mi yoksa yerel bir derleme mi olduğunu gösterir. Bu meta veriler tüm bağımlılıklar için geçerlidir, ancak dosyalar için kullanılamaz. Bu meta veriler için kullanılabilir değerler:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified` , bildirim oluşturucusunu derleme türünü otomatik olarak belirleyecek olan varsayılan değerdir.|
|`Group`|Ek dosyaları isteğe bağlı olarak indirmek için grubu gösterir. Grup adı uygulama tarafından tanımlanır ve herhangi bir dize olabilir. Boş dize, dosyanın varsayılan indirme grubunun parçası olmadığını gösterir. Grupta yer alan dosyalar, ilk uygulama indirme işlemi kapsamındadır. Bir gruptaki dosyalar yalnızca kullanılarak uygulama tarafından açıkça istenen dosyalar <xref:System.Deployment.Application> indirilir.<br /><br /> Bu meta veriler, olan tüm dosyalar `IsDataFile` ve `false` olduğu tüm bağımlılıklar için `DependencyType` `Install` geçerlidir.|
|`TargetPath`|Yolun oluşturulan bildirimde nasıl tanımlanmalıdır olduğunu belirtir. Bu öznitelik tüm dosyalar için geçerlidir. Bu öznitelik belirtilmezse, öğe belirtimi kullanılır. Bu öznitelik değerine sahip tüm dosyalar ve bağımlılıklar `DependencyType` için `Install` geçerlidir.|
|`IsDataFile`|Dosyanın `Boolean` bir veri dosyası olup olmadığını belirten meta veri değeri. Veri dosyası, uygulama güncelleştirmeleri arasında geçirilirken özeldir. Bu meta veriler yalnızca dosyalar için geçerlidir. `False` varsayılan değerdir.|

## <a name="example-1"></a>Örnek 1

Bu örnek, tek bir uygulama bildirimi ClickOnce bir uygulama için dağıtım bildirimi oluşturmak için görevi ve tek bir derleme ile bir dağıtım `GenerateApplicationManifest` bildirimi oluşturmak için görevi `GenerateDeploymentManifest` kullanır. Ardından bildirimleri `SignFile` imzalamak için görevini kullanır.

Bu, tek bir program için bildirim oluşturma ClickOnce mümkün olan en basit bildirim oluşturma senaryosunu gösterir. Bildirim için derlemeden varsayılan bir ad ve kimlik çıkarıldı.

> [!NOTE]
> Aşağıdaki örnekte, bildirim oluşturma yönlerine odaklanmak için tüm uygulama ikilileri önceden hazırlanmıştır. Bu örnek, dağıtım için tam olarak ClickOnce üretir.
>
> [!NOTE]
> Bu örnekteki `Thumbprint` görevde kullanılan özellik hakkında `SignFile` daha fazla bilgi için bkz. [SignFile görevi.](../msbuild/signfile-task.md)

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <EntryPoint Include="SimpleWinApp.exe" />
    </ItemGroup>

    <PropertyGroup>
        <Thumbprint>
             <!-- Insert generated thumbprint here -->
        </Thumbprint>
    </PropertyGroup>

    <Target Name="Build">

        <GenerateApplicationManifest
            EntryPoint="@(EntryPoint)">
            <Output
                ItemName="ApplicationManifest"
                TaskParameter="OutputManifest"/>
        </GenerateApplicationManifest>

        <GenerateDeploymentManifest
            EntryPoint="@(ApplicationManifest)">
            <Output
                ItemName="DeployManifest"
                TaskParameter="OutputManifest"/>
        </GenerateDeploymentManifest>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(ApplicationManifest)"/>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(DeployManifest)"/>

    </Target>
</Project>
```

## <a name="example-2"></a>Örnek 2

Bu örnek, bildirimlerin adını ve ClickOnce belirterek tek bir derlemeye sahip bir uygulama için uygulama ve dağıtım bildirimleri oluşturmak için `GenerateApplicationManifest` ve `GenerateDeploymentManifest` görevlerini kullanır.

Bildirimlerin adı ve kimliği açıkça belirtiliyor dışında bu örnek önceki örnektekine benzer. Ayrıca, bu örnek yüklü bir uygulama yerine çevrimiçi bir uygulama olarak yapılandırılır.

> [!NOTE]
> Aşağıdaki örnekte, bildirim oluşturma yönlerine odaklanmak için tüm uygulama ikilileri önceden hazırlanmıştır. Bu örnek, dağıtım için tam olarak ClickOnce üretir.
>
> [!NOTE]
> Bu örnekteki `Thumbprint` görevde kullanılan özellik hakkında `SignFile` daha fazla bilgi için bkz. [SignFile görevi.](../msbuild/signfile-task.md)

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <EntryPoint Include="SimpleWinApp.exe" />
    </ItemGroup>

    <PropertyGroup>
        <Thumbprint>
             <!-- Insert generated thumbprint here -->
        </Thumbprint>
    </PropertyGroup>

    <Target Name="Build">

        <GenerateApplicationManifest
            AssemblyName="SimpleWinApp.exe"
            AssemblyVersion="1.0.0.0"
            EntryPoint="@(EntryPoint)"
            OutputManifest="SimpleWinApp.exe.manifest">
            <Output
                ItemName="ApplicationManifest"
                TaskParameter="OutputManifest"/>
        </GenerateApplicationManifest>

        <GenerateDeploymentManifest
                AssemblyName="SimpleWinApp.application"
                AssemblyVersion="1.0.0.0"
                EntryPoint="@(ApplicationManifest)"
                Install="false"
                OutputManifest="SimpleWinApp.application">
                <Output
                    ItemName="DeployManifest"
                    TaskParameter="OutputManifest"/>
        </GenerateDeploymentManifest>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(ApplicationManifest)"/>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(DeployManifest)"/>

    </Target>
</Project>
```

## <a name="example-3"></a>Örnek 3

Bu örnekte, birden çok dosya ve derlemeye ClickOnce uygulama ve dağıtım bildirimleri oluşturmak `GenerateApplicationManifest` `GenerateDeploymentManifest` için ve görevleri kullanılır.

> [!NOTE]
> Aşağıdaki örnekte, bildirim oluşturma yönlerine odaklanmak için tüm uygulama ikilileri önceden hazırlanmıştır. Bu örnek, dağıtım için tam olarak ClickOnce üretir.
>
> [!NOTE]
> Bu örnekteki `Thumbprint` görevde kullanılan özellik hakkında `SignFile` daha fazla bilgi için bkz. [SignFile görevi.](../msbuild/signfile-task.md)

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <EntryPoint Include="SimpleWinApp.exe" />
    </ItemGroup>

    <PropertyGroup>
        <Thumbprint>
             <!-- Insert generated thumbprint here -->
        </Thumbprint>
        <DeployUrl>
            <!-- Insert the deployment URL here -->
        </DeployUrl>
        <SupportUrl>
            <!-- Insert the support URL here -->
        </SupportUrl>
    </PropertyGroup>

    <Target Name="Build">

    <ItemGroup>
        <EntryPoint Include="SimpleWinApp.exe"/>
        <Dependency Include="ClassLibrary1.dll">
            <AssemblyType>Managed</AssemblyType>
            <DependencyType>Install</DependencyType>
        </Dependency>
        <Dependency Include="ClassLibrary2.dll">
            <AssemblyType>Managed</AssemblyType>
            <DependencyType>Install</DependencyType>
            <Group>Secondary</Group>
        </Dependency>
        <Dependency Include="MyAddIn1.dll">
            <AssemblyType>Managed</AssemblyType>
            <DependencyType>Install</DependencyType>
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>
        </Dependency>
        <Dependency Include="ClassLibrary3.dll">
            <AssemblyType>Managed</AssemblyType>
            <DependencyType>Prerequisite</DependencyType>
        </Dependency>

        <File Include="Text1.txt">
            <TargetPath>Text\Text1.txt</TargetPath>
            <Group>Text</Group>
        </File>
        <File Include="DataFile1.xml ">
            <TargetPath>Data\DataFile1.xml</TargetPath>
            <IsDataFile>true</IsDataFile>
        </File>

        <IconFile Include="Heart.ico"/>
        <ConfigFile Include="app.config">
            <TargetPath>SimpleWinApp.exe.config</TargetPath>
        </ConfigFile>
        <BaseManifest Include="app.manifest"/>
    </ItemGroup>

    <Target Name="Build">

        <GenerateApplicationManifest
            AssemblyName="SimpleWinApp.exe"
            AssemblyVersion="1.0.0.0"
            ConfigFile="@(ConfigFile)"
            Dependencies="@(Dependency)"
            Description="TestApp"
            EntryPoint="@(EntryPoint)"
            Files="@(File)"
            IconFile="@(IconFile)"
            InputManifest="@(BaseManifest)"
            OutputManifest="SimpleWinApp.exe.manifest">
            <Output
                ItemName="ApplicationManifest"
                TaskParameter="OutputManifest"/>
        </GenerateApplicationManifest>

        <GenerateDeploymentManifest
            AssemblyName="SimpleWinApp.application"
            AssemblyVersion="1.0.0.0"
            DeploymentUrl="$(DeployToUrl)"
            Description="TestDeploy"
            EntryPoint="@(ApplicationManifest)"
            Install="true"
            OutputManifest="SimpleWinApp.application"
            Product="SimpleWinApp"
            Publisher="Microsoft"
            SupportUrl="$(SupportUrl)"
            UpdateEnabled="true"
            UpdateInterval="3"
            UpdateMode="Background"
            UpdateUnit="weeks">
            <Output
                ItemName="DeployManifest"
                TaskParameter="OutputManifest"/>
        </GenerateDeploymentManifest>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(ApplicationManifest)"/>

        <SignFile
            CertificateThumbprint="$(Thumbprint)"
            SigningTarget="@(DeployManifest)"/>

    </Target>
</Project>
```

## <a name="example-4"></a>Örnek 4

Bu örnekte, uygulaması için yerel bir bildirim oluşturmak `GenerateApplicationManifest` için görevi  *Test.exe,* yerel bileşenAlpha.dllve bir yalıtılmış COM bileşenine *Bravo.dll.*

Bu örnek, *Test.exe.manifest'ı* üretir, böylece uygulama XCOPY dağıtılabilir olur ve KayıtSız COM'den faydalanır.

> [!NOTE]
> Aşağıdaki örnekte, bildirim oluşturma yönlerine odaklanmak için tüm uygulama ikilileri önceden hazırlanmıştır. Bu örnek, dağıtım için tam olarak ClickOnce üretir.

```xml
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <File Include="Test.exe" />
        <Dependency Include="Alpha.dll">
            <AssemblyType>Native</AssemblyType>
            <DependencyType>Install</DependencyType>
        </Dependency>
        <ComComponent Include="Bravo.dll" />
    </ItemGroup>

    <Target Name="Build">
        <GenerateApplicationManifest
            AssemblyName="Test.exe"
            AssemblyVersion="1.0.0.0"
            Dependencies="@(Dependency)"
            Files="@(File)"
            IsolatedComReferences="@(ComComponent)"
            ManifestType="Native">
            <Output
                ItemName="ApplicationManifest"
                TaskParameter="OutputManifest"/>
        </GenerateApplicationManifest>

    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [GenerateDeploymentManifest görevi](../msbuild/generatedeploymentmanifest-task.md)
- [SignFile görevi](../msbuild/signfile-task.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
