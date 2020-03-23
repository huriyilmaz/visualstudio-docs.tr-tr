---
title: OluşturmaUygulamaBildirimi Görev | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634103"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest görevi

ClickOnce uygulama bildirimi veya yerel bir bildirim oluşturur. Yerel bir bildirim, bileşen için benzersiz bir kimlik tanımlayarak ve bileşeni oluşturan tüm derlemeleri ve dosyaları tanımlayarak bir bileşeni açıklar. ClickOnce uygulama bildirimi, uygulamanın giriş noktasını belirterek ve uygulama güvenlik düzeyini belirterek yerel bir manifestoyu genişletir.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görev parametreleri `GenerateApplicationManifest` açıklanmaktadır.

| Parametre | Açıklama |
|---------------------------------| - |
| `AssemblyName` | İsteğe bağlı `String` parametre.<br /><br /> Oluşturulan bildirim `Name` için derleme kimliğinin alanını belirtir. Bu parametre belirtilmemişse, ad veya `EntryPoint` `InputManifest` parametrelerden çıkarılır. Ad oluşturulamazsa, görev bir hata atar. |
| `AssemblyVersion` | İsteğe bağlı `String` parametre.<br /><br /> Oluşturulan bildirim `Version` için derleme kimliğinin alanını belirtir. Bu parametre belirtilmemişse, varsayılan değer "1.0.0.0" kullanılır. |
| `ClrVersion` | İsteğe bağlı `String` parametre.<br /><br /> Uygulama tarafından gerekli olan Ortak Dil Çalışma Süresi'nin (CLR) en az sürümünü belirtir. Varsayılan değer, yapı sistemi tarafından kullanılan CLR sürümüdür. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır. |
| `ConfigFile` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Hangi öğenin uygulama yapılandırma dosyasını içerdiğini belirtir. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır. |
| `Dependencies` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Oluşturulan bildirim için bağımlı derlemeler kümesini tanımlayan bir madde listesi belirtir. Her öğe, ek dağıtım durumunu ve bağımlılık türünü belirtmek için madde meta verileri tarafından daha fazla tanımlanabilir. Daha fazla bilgi için [Madde meta verilerine](#item-metadata)bakın. |
| `Description` | İsteğe bağlı `String` parametre.<br /><br /> Uygulama veya bileşenin açıklamasını belirtir. |
| `EntryPoint` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Oluşturulan bildirim derlemesinin giriş noktasını gösteren tek bir öğe belirtir.<br /><br /> ClickOnce uygulama bildirimi için bu parametre, uygulama çalıştırıldığında başlayan derlemeyi belirtir. |
| `ErrorReportUrl` | İsteğe bağlı <xref:System.String?displayProperty=fullName> parametre.<br /><br /> ClickOnce yüklemelerinde hata raporları sırasında iletişim kutularında görüntülenen web sayfasının URL'sini belirtir. |
| `FileAssociations` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> ClickOnce dağıtım bildirimiyle ilişkili bir veya daha fazla dosya türünün listesini belirtir.<br /><br /> Dosya ilişkilendirmeleri yalnızca .NET Framework 3.5 veya sonraki hedeflendiğinde geçerlidir. |
| `Files` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bildirime dahil edilen dosyalar. Her dosya için tam yolu belirtin. |
| `HostInBrowser` | İsteğe bağlı <xref:System.Boolean> parametre.<br /><br /> `true`Uygulama bir tarayıcıda barındırılıyorsa (WPF Web TarayıcıSı Uygulamaları gibi). |
| `IconFile` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Uygulama simgesi dosyasını gösterir. Uygulama simgesi oluşturulan uygulama bildiriminde ifade edilir ve **Başlat Menüsü** ve **Programları Ekle/Kaldır** iletişim kutusu için kullanılır. Bu giriş belirtilmemişse, varsayılan bir simge kullanılır. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır. |
| `InputManifest` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Manifest jeneratör için bir temel olarak hizmet vermek için bir giriş XML belge gösterir. Bu, uygulama güvenliği veya özel bildirim tanımları gibi yapılandırılmış verilerin çıktı bildirimine yansıtılmasını sağlar. XML belgesindeki kök öğe asmv1 ad alanında bir derleme düğümü olmalıdır. |
| `IsolatedComReferences` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Oluşturulan bildirimde yalıtmak için COM bileşenlerini belirtir. Bu parametre, "Kayıt Ücretsiz COM" dağıtımı için COM bileşenlerini yalıtma yeteneğini destekler. Standart COM kayıt tanımlarına sahip bir manifestootomatik oluşturarak çalışır. Ancak, bunun düzgün çalışması için COM bileşenlerinin yapı makinesine kaydedilmesi gerekir. |
| `ManifestType` | İsteğe bağlı `String` parametre.<br /><br /> Hangi manifesto türünü oluşturacağıbelirtilir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Bu parametre belirtilmemişse, görev `ClickOnce`varsayılan olarak . |
| `MaxTargetPath` | İsteğe bağlı `String` parametre.<br /><br /> ClickOnce uygulama dağıtımında dosya yolunun izin verilen maksimum uzunluğunu belirtir. Bu değer belirtilirse, uygulamadaki her dosya yolunun uzunluğu bu sınıra göre denetlenir. Sınırı aşan tüm öğeler bir yapı uyarısı yükseltecektir. Bu giriş belirtilmemişse veya sıfır ise, denetim yapılmaz. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır. |
| `OSVersion` | İsteğe bağlı `String` parametre.<br /><br /> Uygulama nın gerektirdiği minimum gerekli işletim sistemi (OS) sürümünü belirtir. Örneğin, "5.1.2600.0" değeri işletim sisteminin Windows XP olduğunu gösterir. Bu parametre belirtilmemişse, .NET Framework'ün en az desteklenen işletim sistemi olan Windows 98 Second Edition'ı gösteren "4.10.0.0" değeri kullanılır. Görev yerel bir bildirim oluşturuyorsa, bu giriş yoksayılır. |
| `OutputManifest` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıktı parametresi.<br /><br /> Oluşturulan çıktı bildirimi dosyasının adını belirtir. Bu parametre belirtilmemişse, çıktı dosyasının adı oluşturulan bildirimin kimliğinden çıkarılır. |
| `Platform` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın hedef platformını belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Bu parametre belirtilmemişse, görev `AnyCPU`varsayılan olarak . |
| `Product` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın adını belirtir. Bu parametre belirtilmemişse, ad oluşturulan bildirimin kimliğinden çıkarılır. Bu **ad, Başlat** menüsündeki kısayol adı için kullanılır ve **Programlar Ekle veya Kaldır** iletişim kutusunda görünen adın bir parçasıdır. |
| `Publisher` | İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın yayımcısını belirtir. Bu parametre belirtilmemişse, ad kayıtlı kullanıcıdan veya oluşturulan bildirimin kimliğinden çıkarılır. Bu ad **Başlat** menüsündeki klasör adı için kullanılır ve Programlar Ekle **veya Kaldır** iletişim kutusunda görünen adın bir parçasıdır. |
| `RequiresMinimumFramework35SP1` | İsteğe bağlı `Boolean` parametre.<br /><br /> Doğruysa, uygulama .NET Framework 3.5 SP1 veya daha yeni bir sürüm gerektirir. |
| `TargetCulture` | İsteğe bağlı `String` parametre.<br /><br /> Uygulama kültürünü tanımlar ve oluşturulan bildirim `Language` için derleme kimliğinin alanını belirtir. Bu parametre belirtilmemişse, uygulamanın kültür değişmezi olduğu varsayılır. |
| `TargetFrameworkMoniker` | İsteğe bağlı `String` parametre.<br /><br /> Hedef çerçeve takma adacını belirtir. |
| `TargetFrameworkProfile` | İsteğe bağlı `String` parametre.<br /><br /> Hedef çerçeve profilini belirtir. |
| `TargetFrameworkSubset` | İsteğe bağlı `String` parametre.<br /><br /> Hedef için .NET Framework alt kümesinin adını belirtir. |
| `TargetFrameworkVersion` | İsteğe bağlı `String` parametre.<br /><br /> Projenin hedefini .NET Framework belirtir. |
| `TrustInfoFile` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Uygulama güvenliğini belirten bir XML belgesini gösterir. XML belgesindeki kök öğe asmv2 ad alanında bir trustInfo düğümü olmalıdır. Görev yerel bir bildirim oluşturuyorsa, bu parametre yoksayılır. |
| `UseApplicationTrust` | İsteğe bağlı `Boolean` parametre.<br /><br /> Doğruysa, `Product`, `Publisher`, `SupportUrl` ve özellikleri uygulama bildirimine yazılır. |

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.GenerateManifestBase> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Görev sınıfının parametrelerinin listesi için [Görev taban sınıfına](../msbuild/task-base-class.md)bakın.

Görevin `GenerateDeploymentManifest` nasıl kullanılacağı hakkında bilgi için [bkz.](../msbuild/generateapplicationmanifest-task.md)

Bağımlılıklar ve dosyalar için girişler, her öğe için ek dağıtım durumu belirtmek için madde meta verileriyle daha da dekore edilebilir.

## <a name="item-metadata"></a>Madde meta verileri

|Meta veri adı|Açıklama|
|-------------------|-----------------|
|`DependencyType`|Bağımlılığın uygulamayla mı yoksa ön koşulla mı yayınlanıp yüklenmediğini gösterir. Bu meta veriler tüm bağımlılıklar için geçerlidir, ancak dosyalar için kullanılmaz. Bu meta veriler için kullanılabilir değerler şunlardır:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Yükleme varsayılan değerdir.|
|`AssemblyType`|Bağımlılığın yönetilen mi yoksa yerel bir derleme mi olduğunu gösterir. Bu meta veriler tüm bağımlılıklar için geçerlidir, ancak dosyalar için kullanılmaz. Bu meta veriler için kullanılabilir değerler şunlardır:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified`varsayılan değerdir, bu da bildirim üretecinin montaj türünü otomatik olarak belirleyeceğini gösterir.|
|`Group`|İsteğe bağlı ek dosya indirmek için grubu gösterir. Grup adı uygulama tarafından tanımlanır ve herhangi bir dize olabilir. Boş bir dize, dosyanın varsayılan olan bir karşıdan yükleme grubunun parçası olmadığını gösterir. Bir grupta olmayan dosyalar ilk uygulama indirmesinin bir parçasıdır. Bir gruptaki dosyalar yalnızca uygulama tarafından açıkça istendiğinde <xref:System.Deployment.Application>indirilir.<br /><br /> Bu meta veriler, nerede `IsDataFile` olduğu `false` ve tüm `DependencyType` bağımlılıkları nerede tüm dosyalar için geçerlidir. `Install`|
|`TargetPath`|Oluşturulan bildirimde yolun nasıl tanımlandığını belirtir. Bu öznitelik tüm dosyalar için geçerlidir. Bu öznitelik belirtilmemişse, madde belirtimi kullanılır. Bu öznitelik, `DependencyType` `Install`değeri olan tüm dosyalar ve bağımlılıklar için geçerlidir.|
|`IsDataFile`|Dosyanın bir veri dosyası olup olmadığını gösteren bir `Boolean` meta veri değeri. Bir veri dosyası, uygulama güncelleştirmeleri arasında geçirilir olması açısından özeldir. Bu meta veriler yalnızca dosyalar için geçerlidir. `False`varsayılan değerdir.|

## <a name="example"></a>Örnek

Bu örnek, `GenerateApplicationManifest` bir ClickOnce uygulama bildirimi `GenerateDeploymentManifest` ve tek bir derleme ile bir uygulama için bir dağıtım bildirimi oluşturmak için görev oluşturmak için görevi kullanır. Daha sonra `SignFile` bildirimleri imzalamak için görevi kullanır.

Bu, ClickOnce bildirimlerinin tek bir program için oluşturulduğu olası en basit bildirim oluşturma senaryosunu gösterir. Varsayılan ad ve kimlik, bildirim için derlemeden çıkarılır.

> [!NOTE]
> Aşağıdaki örnekte, tüm uygulama ikilileri, manifesto oluşturma yönlerine odaklanmak için önceden oluşturulmuştür. Bu örnek, tam olarak çalışan bir ClickOnce dağıtımı üretir.
>
> [!NOTE]
> Bu örnekte `Thumbprint` `SignFile` görevde kullanılan özellik hakkında daha fazla bilgi için [SignFile görevine](../msbuild/signfile-task.md)bakın.

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

Bu örnek, `GenerateApplicationManifest` `GenerateDeploymentManifest` bildirimlerin adını ve kimliğini belirten tek bir derlemeye sahip bir uygulama için ClickOnce uygulama ve dağıtım bildirimlerini oluşturmak için görevleri kullanır.

Bu örnek, bildirimlerin adı ve kimliği açıkça belirtilmediak önceki örneğe benzer. Ayrıca, bu örnek yüklü bir uygulama yerine çevrimiçi bir uygulama olarak yapılandırılır.

> [!NOTE]
> Aşağıdaki örnekte, tüm uygulama ikilileri, manifesto oluşturma yönlerine odaklanmak için önceden oluşturulmuştür. Bu örnek, tam olarak çalışan bir ClickOnce dağıtımı üretir.
>
> [!NOTE]
> Bu örnekte `Thumbprint` `SignFile` görevde kullanılan özellik hakkında daha fazla bilgi için [SignFile görevine](../msbuild/signfile-task.md)bakın.

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

Bu örnek, `GenerateApplicationManifest` `GenerateDeploymentManifest` birden çok dosya ve derlemeiçeren bir uygulama için ClickOnce uygulama ve dağıtım bildirimleri oluşturmak için görevleri kullanır.

> [!NOTE]
> Aşağıdaki örnekte, tüm uygulama ikilileri, manifesto oluşturma yönlerine odaklanmak için önceden oluşturulmuştür. Bu örnek, tam olarak çalışan bir ClickOnce dağıtımı üretir.
>
> [!NOTE]
> Bu örnekte `Thumbprint` `SignFile` görevde kullanılan özellik hakkında daha fazla bilgi için [SignFile görevine](../msbuild/signfile-task.md)bakın.

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

Bu örnek, `GenerateApplicationManifest` uygulama *Test.exe*için yerel bir manifesto oluşturmak için görevi kullanır, yerel bileşen *Alpha.dll* ve yalıtılmış com bileşeni *Bravo.dll*başvurur.

Bu örnek, Uygulama XCOPY dağıtılabilir hale ve Kayıt Ücretsiz COM *yararlanarak, Test.exe.manifest*üretir.

> [!NOTE]
> Aşağıdaki örnekte, tüm uygulama ikilileri, manifesto oluşturma yönlerine odaklanmak için önceden oluşturulmuştür. Bu örnek, tam olarak çalışan bir ClickOnce dağıtımı üretir.

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
- [DeploymentManifest görev oluşturma](../msbuild/generatedeploymentmanifest-task.md)
- [SignFile görevi](../msbuild/signfile-task.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
