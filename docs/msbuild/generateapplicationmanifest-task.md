---
title: GenerateApplicationManifest görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f77420c5ab269e1b0052ce6102c4e3196a3be52b
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634103"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest görevi

ClickOnce uygulama bildirimi veya yerel bildirim oluşturur. Yerel bildirim bileşeni, bileşen için benzersiz bir kimlik tanımlayarak ve bileşeni oluşturan tüm derlemeleri ve dosyaları tanımlayarak bir bileşeni tanımlar. ClickOnce uygulama bildirimi, uygulamanın giriş noktasını belirterek ve uygulama güvenlik düzeyini belirterek yerel bir bildirimi genişletir.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda `GenerateApplicationManifest` görevinin parametreleri açıklanmaktadır.

| Parametre | Açıklama |
|---------------------------------| - |
| `AssemblyName` | İsteğe bağlı `String` parametresi.<br /><br /> Oluşturulan bildirim için derleme kimliğinin `Name` alanını belirtir. Bu parametre belirtilmemişse, ad `EntryPoint` veya `InputManifest` parametrelerinden algılanır. Ad oluşturuoluşturulamadığı takdirde, görev bir hata oluşturur. |
| `AssemblyVersion` | İsteğe bağlı `String` parametresi.<br /><br /> Oluşturulan bildirim için derleme kimliğinin `Version` alanını belirtir. Bu parametre belirtilmemişse, varsayılan "1.0.0.0" değeri kullanılır. |
| `ClrVersion` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın gerektirdiği ortak dil çalışma zamanının (CLR) en düşük sürümünü belirtir. Varsayılan değer, yapı sistemi tarafından kullanılan CLR sürümüdür. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır. |
| `ConfigFile` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Hangi öğenin uygulama yapılandırma dosyasını içerdiğini belirtir. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır. |
| `Dependencies` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Oluşturulan bildirim için bağımlı derlemelerin kümesini tanımlayan bir öğe listesini belirtir. Her öğe, ek dağıtım durumu ve bağımlılık türü belirtmek için öğe meta verileri tarafından daha ayrıntılı bir şekilde açıklanabilir. Daha fazla bilgi için bkz. [öğe meta verileri](#item-metadata). |
| `Description` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulama veya bileşen için açıklama belirtir. |
| `EntryPoint` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Oluşturulan bildirim derlemesi için giriş noktasını gösteren tek bir öğeyi belirtir.<br /><br /> ClickOnce uygulama bildirimi için, bu parametre uygulama çalıştırıldığında başlayan derlemeyi belirtir. |
| `ErrorReportUrl` | İsteğe bağlı <xref:System.String?displayProperty=fullName> parametresi.<br /><br /> ClickOnce yüklemelerinde hata raporları sırasında iletişim kutularında görüntülenen Web sayfasının URL 'sini belirtir. |
| `FileAssociations` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> ClickOnce dağıtım bildirimiyle ilişkili bir veya daha fazla dosya türünün listesini belirtir.<br /><br /> Dosya ilişkilendirmeleri yalnızca .NET Framework 3,5 veya üzeri hedeflenirse geçerlidir. |
| `Files` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Bildirime dahil edilecek dosyalar. Her dosyanın tam yolunu belirtin. |
| `HostInBrowser` | İsteğe bağlı <xref:System.Boolean> parametresi.<br /><br /> `true`, uygulama bir tarayıcıda barındırılır (WPF Web tarayıcısı uygulamaları gibi). |
| `IconFile` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Uygulama simge dosyasını gösterir. Uygulama simgesi oluşturulan uygulama bildiriminde ifade edilir ve **Başlat menüsü** ve **Program Ekle/Kaldır** iletişim kutusu için kullanılır. Bu giriş belirtilmemişse, varsayılan bir simge kullanılır. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır. |
| `InputManifest` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Bildirim Oluşturucu için temel olarak hizmet veren bir giriş XML belgesi gösterir. Bu, uygulama güvenliği veya özel bildirim tanımları gibi yapılandırılmış verilerin çıktı bildiriminde yansıtılmasına olanak tanır. XML belgesindeki kök öğesi asmv1 ad alanında bir derleme düğümü olmalıdır. |
| `IsolatedComReferences` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Oluşturulan bildirimde yalıtmak için COM bileşenlerini belirtir. Bu parametre, "kayıt ücretsiz COM" dağıtımı için COM bileşenlerini yalıtma yeteneğini destekler. Standart COM kayıt tanımlarına sahip bir bildirimi otomatik olarak oluşturarak işe yarar. Ancak, bunun düzgün çalışması için COM bileşenlerinin derleme makinesinde kayıtlı olması gerekir. |
| `ManifestType` | İsteğe bağlı `String` parametresi.<br /><br /> Oluşturulacak bildirim türünü belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Bu parametre belirtilmezse, görev varsayılan olarak `ClickOnce`. |
| `MaxTargetPath` | İsteğe bağlı `String` parametresi.<br /><br /> ClickOnce uygulama dağıtımında bir dosya yolunun izin verilen maksimum uzunluğunu belirtir. Bu değer belirtilmişse, uygulamadaki her dosya yolunun uzunluğu bu sınıra karşı denetlenir. Sınırı aşan öğeler bir yapı uyarısında oluşturulur. Bu giriş belirtilmezse veya sıfırsa hiçbir denetim yapılmaz. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır. |
| `OSVersion` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın gerektirdiği en düşük işletim sistemi (OS) sürümünü belirtir. Örneğin, "5.1.2600.0" değeri işletim sisteminin Windows XP olduğunu gösterir. Bu parametre belirtilmezse, en düşük desteklenen işletim .NET Framework sistemi olan Windows 98 Second Edition 'ı gösteren "4.10.0.0" değeri kullanılır. Görev yerel bir bildirim oluşturuyorsa bu giriş yok sayılır. |
| `OutputManifest` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> Oluşturulan çıkış bildirimi dosyasının adını belirtir. Bu parametre belirtilmemişse, çıkış dosyasının adı oluşturulan bildirimin kimliğinden algılanır. |
| `Platform` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın hedef platformunu belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Bu parametre belirtilmezse, görev varsayılan olarak `AnyCPU`. |
| `Product` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın adını belirtir. Bu parametre belirtilmemişse, ad oluşturulan bildirimin kimliğinden algılanır. Bu ad, **Başlangıç** menüsündeki kısayol adı için kullanılır ve **Program Ekle veya Kaldır** iletişim kutusunda görünen adın bir parçasıdır. |
| `Publisher` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın yayımcısını belirtir. Bu parametre belirtilmemişse, ad kayıtlı kullanıcıdan veya oluşturulan bildirimin kimliğiyle algılanır. Bu ad, **Başlangıç** menüsündeki klasör adı için kullanılır ve **Program Ekle veya Kaldır** iletişim kutusunda görünen adın bir parçasıdır. |
| `RequiresMinimumFramework35SP1` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Doğru ise, uygulama .NET Framework 3,5 SP1 veya daha yeni bir sürümü gerektirir. |
| `TargetCulture` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın kültürünü tanımlar ve oluşturulan bildirim için derleme kimliğinin `Language` alanını belirtir. Bu parametre belirtilmezse, uygulamanın kültür sabiti olduğu varsayılır. |
| `TargetFrameworkMoniker` | İsteğe bağlı `String` parametresi.<br /><br /> Hedef çerçevenin bilinen adını belirtir. |
| `TargetFrameworkProfile` | İsteğe bağlı `String` parametresi.<br /><br /> Hedef çerçeve profilini belirtir. |
| `TargetFrameworkSubset` | İsteğe bağlı `String` parametresi.<br /><br /> Hedeflenecek .NET Framework alt kümesinin adını belirtir. |
| `TargetFrameworkVersion` | İsteğe bağlı `String` parametresi.<br /><br /> Projenin hedef .NET Framework belirtir. |
| `TrustInfoFile` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Uygulama güvenliğini belirten bir XML belgesi gösterir. XML belgesindeki kök öğesi asmv2 ad alanında TrustInfo düğümü olmalıdır. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır. |
| `UseApplicationTrust` | İsteğe bağlı `Boolean` parametresi.<br /><br /> True ise `Product`, `Publisher`ve `SupportUrl` özellikleri uygulama bildirimine yazılır. |

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.GenerateManifestBase> sınıfından parametreleri devralır. Görev sınıfının parametrelerinin listesi için bkz. [görev temel sınıfı](../msbuild/task-base-class.md).

`GenerateDeploymentManifest` görevinin kullanımı hakkında daha fazla bilgi için bkz. [GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md).

Bağımlılıklar ve dosyalar için girişler, her öğe için ek dağıtım durumu belirtmek üzere öğe meta verileri ile birlikte daha da oluşturulabilir.

## <a name="item-metadata"></a>Öğe meta verileri

|Meta veri adı|Açıklama|
|-------------------|-----------------|
|`DependencyType`|Bağımlılığın uygulama veya ön koşul ile yayımlanıp yayımlanmadığını ve yüklenip yüklenmediğini belirtir. Bu meta veriler tüm bağımlılıklar için geçerlidir, ancak dosyalar için kullanılmaz. Bu meta veriler için kullanılabilir değerler şunlardır:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Varsayılan değer Install değeridir.|
|`AssemblyType`|Bağımlılığın yönetilen mi yoksa yerel derleme mi olduğunu gösterir. Bu meta veriler tüm bağımlılıklar için geçerlidir, ancak dosyalar için kullanılmaz. Bu meta veriler için kullanılabilir değerler şunlardır:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified`, bildirim oluşturucunun derleme türünü otomatik olarak belirleyeceğini gösteren varsayılan değerdir.|
|`Group`|İsteğe bağlı ek dosyaları indirme grubunu gösterir. Grup adı uygulama tarafından tanımlanır ve herhangi bir dize olabilir. Boş bir dize, dosyanın varsayılan olan bir indirme grubunun parçası olmadığını gösterir. Bir grupta olmayan dosyalar ilk uygulama indirmenin bir parçasıdır. Bir gruptaki dosyalar yalnızca <xref:System.Deployment.Application>kullanılarak uygulama tarafından açıkça istendiğinde indirilir.<br /><br /> Bu meta veriler, `IsDataFile` `false` ve `DependencyType` `Install`olduğu tüm bağımlılıklar için geçerlidir.|
|`TargetPath`|Yolun oluşturulan bildirimde nasıl tanımlanması gerektiğini belirtir. Bu öznitelik tüm dosyalar için geçerlidir. Bu öznitelik belirtilmemişse, öğe belirtimi kullanılır. Bu öznitelik, `Install``DependencyType` değerine sahip tüm dosyalar ve Bağımlılıklar için geçerlidir.|
|`IsDataFile`|Dosyanın bir veri dosyası olup olmadığını gösteren `Boolean` meta veri değeri. Bir veri dosyası, uygulama güncelleştirmeleri arasında geçirilme için özeldir. Bu meta veriler yalnızca dosyalar için geçerlidir. Varsayılan değer `False`.|

## <a name="example"></a>Örnek

Bu örnek, bir ClickOnce uygulama bildirimi oluşturmak için `GenerateApplicationManifest` görevini ve tek bir bütünleştirilmiş koda sahip bir uygulama için dağıtım bildirimi oluşturmak üzere `GenerateDeploymentManifest` görevini kullanır. Daha sonra bildirimleri imzalamak için `SignFile` görevini kullanır.

Bu, tek bir program için ClickOnce bildirimlerinin oluşturulduğu en basit olası bildirim oluşturma senaryosunu gösterir. Bildirim için derlemeden varsayılan bir ad ve kimlik algılanır.

> [!NOTE]
> Aşağıdaki örnekte, tüm uygulama ikilileri bildirim oluşturma yönlerine odaklanmak için önceden oluşturulmuştur. Bu örnek, tam olarak çalışan bir ClickOnce dağıtımı üretir.
>
> [!NOTE]
> Bu örnekteki `SignFile` görevinde kullanılan `Thumbprint` özelliği hakkında daha fazla bilgi için bkz. [SignFile görevi](../msbuild/signfile-task.md).

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

## <a name="example"></a>Örnek

Bu örnekte, bildirimlerin ad ve kimliğini belirterek tek bir bütünleştirilmiş koda sahip bir uygulama için ClickOnce uygulaması ve dağıtım bildirimleri oluşturmak üzere `GenerateApplicationManifest` ve `GenerateDeploymentManifest` görevleri kullanılmaktadır.

Bu örnek, bildirimlerin adı ve kimliği açıkça belirtildiğinde, önceki örneğe benzerdir. Ayrıca, bu örnek yüklü bir uygulama yerine çevrimiçi bir uygulama olarak yapılandırılır.

> [!NOTE]
> Aşağıdaki örnekte, tüm uygulama ikilileri bildirim oluşturma yönlerine odaklanmak için önceden oluşturulmuştur. Bu örnek, tam olarak çalışan bir ClickOnce dağıtımı üretir.
>
> [!NOTE]
> Bu örnekteki `SignFile` görevinde kullanılan `Thumbprint` özelliği hakkında daha fazla bilgi için bkz. [SignFile görevi](../msbuild/signfile-task.md).

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

## <a name="example"></a>Örnek

Bu örnek, birden çok dosya ve derlemeye sahip bir uygulama için ClickOnce uygulaması ve dağıtım bildirimleri oluşturmak üzere `GenerateApplicationManifest` ve `GenerateDeploymentManifest` görevlerini kullanır.

> [!NOTE]
> Aşağıdaki örnekte, tüm uygulama ikilileri bildirim oluşturma yönlerine odaklanmak için önceden oluşturulmuştur. Bu örnek, tam olarak çalışan bir ClickOnce dağıtımı üretir.
>
> [!NOTE]
> Bu örnekteki `SignFile` görevinde kullanılan `Thumbprint` özelliği hakkında daha fazla bilgi için bkz. [SignFile görevi](../msbuild/signfile-task.md).

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

## <a name="example"></a>Örnek

Bu örnek, yerel bileşen *Alpha. dll* ve YALıTıLMıŞ bir com bileşeni *Bravo. dll*' ye başvuran uygulama *test. exe*için yerel bir bildirim oluşturmak üzere `GenerateApplicationManifest` görevini kullanır.

Bu örnek, *test. exe. manifest*dosyasını üretir, böylece uygulama xcopy olarak dağıtılabilir ve kayıt ücretsiz com avantajlarından yararlanır.

> [!NOTE]
> Aşağıdaki örnekte, tüm uygulama ikilileri bildirim oluşturma yönlerine odaklanmak için önceden oluşturulmuştur. Bu örnek, tam olarak çalışan bir ClickOnce dağıtımı üretir.

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
