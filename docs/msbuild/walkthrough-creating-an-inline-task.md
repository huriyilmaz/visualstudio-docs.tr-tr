---
title: 'Adım adım kılavuz: Satır Içi Görev | Microsoft Docs'
description: Görevi barındırmak için MSBuild derleme oluşturmak zorunda kalmadan proje dosyasında satır içi bir görev oluşturma adımlarını adım adım gösterir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
- MSBuild, tasks
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: d2f48dc054a4b3523a6c2a8ac644029fa2385b6ef05c41fcc64d124ae87e2c3c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397143"
---
# <a name="walkthrough-create-an-inline-task"></a>Adım adım kılavuz: Satır içi görev oluşturma

MSBuild görevleri genellikle arabirimi uygulayan bir sınıf oluşturularak <xref:Microsoft.Build.Framework.ITask> oluşturulur. 4. .NET Framework başlayarak proje dosyasında satır içi görevler oluşturabilirsiniz. Görevi barındırmak için ayrı bir derleme oluşturmanıza gerek yok. Daha fazla bilgi için [bkz. Satır içi görevler.](../msbuild/msbuild-inline-tasks.md)

 Bu kılavuzda, bu satır içi görevlerin nasıl oluşturulacak ve çalıştırılır:

- Giriş veya çıkış parametresine sahip bir görev.

- Tek bir giriş parametresi olan ve çıkış parametresine sahip bir görev.

- İki giriş parametresine sahip bir görev ve bir çıkış parametresi, iki giriş MSBuild döndürür.

- İki giriş parametresine sahip bir görev ve bir çıkış parametresi, iki giriş MSBuild döndürür.

Görevleri oluşturmak ve çalıştırmak için Visual Studio komut **Visual Studio komut istemi penceresini aşağıdaki** gibi kullanın:

1. Visual Studio kullanarak MSBuild proje dosyası Visual Studio.

2. Satır içi görevi oluşturmak Visual Studio proje dosyasını değiştirme.

3. Projeyi **derlemek ve sonuçları** incelemek için Komut İstemi Penceresi'ne tıklayın.

## <a name="create-and-modify-an-msbuild-project"></a>MSBuild projesi oluşturma ve değiştirme

 Visual Studio proje sistemi MSBuild'i temel alır. Bu nedenle, bir derleme proje dosyası oluşturmak için Visual Studio. Bu bölümde, bir Visual C# proje dosyası oluşturun. (Bunun yerine bir Visual Basic dosyası oluşturabilirsiniz. Bu öğretici bağlamında, iki proje dosyası arasındaki fark küçük olur.)

#### <a name="to-create-and-modify-a-project-file"></a>Proje dosyası oluşturmak ve değiştirmek için

1. Bu Visual Studio, C# ve Forms Uygulaması şablonunu **Windows yeni bir proje** oluşturun. **Ad** kutusuna `InlineTasks` yazın. Çözüm **için** bir Konum yazın, örneğin *D: \\*. Çözüm için **dizin oluştur'un seçili** olduğundan, **Kaynak Denetimine Ekle'nin** temiz olduğundan ve Çözüm **Adı'nın InlineTasks olduğundan emin olun.** 

3. Proje **dosyasını** oluşturmak için Tamam'a tıklayın.

3. Bu **Çözüm Gezgini,** **InlineTasks** proje düğümüne sağ tıklayın ve ardından Yüklemeden **kaldır'a Project.**

4. Proje düğümüne yeniden sağ tıklayın ve ardından **InlineTasks.csproj öğesini düzenle'ye tıklayın.**

     Proje dosyası kod düzenleyicisinde görüntülenir.

## <a name="add-a-basic-hello-task"></a>Temel bir Merhaba görevi ekleme

 Şimdi proje dosyasına "Hello, world!" iletisi görüntüleyen basit bir görev ekleyin Ayrıca görevi çağırmak için varsayılan bir TestBuild hedefi ekleyin.

#### <a name="to-add-a-basic-hello-task"></a>Temel bir Merhaba görevi eklemek için

1. Kök `Project` düğümde özniteliğini `DefaultTargets` olarak `TestBuild` değiştirebilirsiniz. Sonuçta elde `Project` edilen düğüm şu örnekteki gibi bir sonuç elde edilebilir:

   ```xml
   <Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   ```

2. Aşağıdaki satır içi görevi ve hedefi etiketinin hemen öncesinde proje dosyasına `</Project>` ekleyin.

   ```xml
   <UsingTask TaskName="Hello" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup />
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, "Hello, world!");
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Hello />
   </Target>
   ```

3. Proje dosyasını kaydedin.

   Bu kod, Hello adlı bir satır içi görev oluşturur ve hiçbir parametresi, başvurusu veya `Using` yönergesi yoktur. Hello görevi, varsayılan günlük kaydı cihazında (genellikle konsol penceresi) bir merhaba iletisi görüntüleyen tek bir kod satırı içerir.

### <a name="run-the-hello-task"></a>Hello görevini çalıştırma

 Hello MSBuild oluşturmak **ve** çağıran TestBuild hedefini çalıştırmak için Komut İstemi Penceresini kullanarak komut istemini çalıştırın.

##### <a name="to-run-the-hello-task"></a>Hello görevini çalıştırmak için

1. **Başlat'a** tıklayın, **Tüm Programlar'a** tıklayın, **ardından Visual Studio Araçları** klasörünü bulun ve **Komut İstemi'Visual Studio'ye tıklayın.**

2. Komut **İstemi Penceresinde,** proje dosyasını içeren klasörü (bu durumda *D:\InlineTasks\InlineTasks) bulun. \\*

3. Komut **anahtarları olmadan msbuild** yazın ve Enter tuşuna **basın.** Varsayılan olarak, *InlineTasks.csproj* dosyasını derler ve Hello görevini çağıran varsayılan hedef TestBuild'i işler.

4. Komut İstemi **Penceresindeki çıktıyı inceleme.** Şu satırı görmeniz gerekir:

    `Hello, world!`

   > [!NOTE]
   > Merhaba iletiyi görmüyorsanız proje dosyasını kaydetmeyi yeniden deneyin ve Hello görevini çalıştırın.

   Kod düzenleyicisi ile Komut İstemi Penceresi arasında değişiklikerek proje dosyasını değiştirebilir ve sonuçları hızla görebilirsiniz.

## <a name="define-the-echo-task"></a>Echo görevini tanımlama

 Bir dize parametresi kabul eden ve dizeyi varsayılan günlük cihazında görüntüleyen bir satır içi görev oluşturun.

#### <a name="to-define-the-echo-task"></a>Echo görevini tanımlamak için

1. Kod düzenleyicisinde, aşağıdaki kodu kullanarak Hello görevini ve TestBuild hedefini değiştirin.

   ```xml
   <UsingTask TaskName="Echo" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Text Required="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, Text);
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Echo Text="Greetings!" />
   </Target>
   ```

2. Komut **İstemi Penceresi'ne** komut anahtarları olmadan **msbuild** yazın ve Enter tuşuna **basın.** Varsayılan olarak, bu, Echo görevini çağıran varsayılan hedef TestBuild'i işler.

3. Komut İstemi **Penceresindeki çıktıyı inceleme.** Şu satırı görmeniz gerekir:

    `Greetings!`

   Bu kod Echo adlı ve yalnızca bir gerekli giriş parametresi Text olan bir satır içi görevi tanımlar. Varsayılan olarak, parametreler System.String türündedir. TestBuild hedefi Echo görevini çağıran Text parametresinin değeri ayarlanır.

## <a name="define-the-adder-task"></a>Adder görevini tanımlama

 İki tamsayı parametresi ekleyen ve toplamlarını bir tamsayı özelliği olarak yayan bir satır içi MSBuild oluşturun.

#### <a name="to-define-the-adder-task"></a>Adder görevini tanımlamak için

1. Kod düzenleyicisinde aşağıdaki kodu kullanarak Echo görevini ve TestBuild hedefini değiştirin.

   ```xml
   <UsingTask TaskName="Adder" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <A ParameterType="System.Int32" Required="true" />
       <B ParameterType="System.Int32" Required="true" />
       <C ParameterType="System.Int32" Output="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         C = A + B;
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Adder A="4" B="5">
       <Output PropertyName="Sum" TaskParameter="C" />
     </Adder>
     <Message Text="The sum is $(Sum)" Importance="High" />
   </Target>
   ```

2. Komut **İstemi Penceresi'ne** komut anahtarları olmadan **msbuild** yazın ve Enter tuşuna **basın.** Varsayılan olarak, bu, Echo görevini çağıran varsayılan hedef TestBuild'i işler.

3. Komut İstemi **Penceresindeki çıktıyı inceleme.** Şu satırı görmeniz gerekir:

    `The sum is 9`

   Bu kod, Adder adlı bir satır içi görevi tanımlar ve iki gerekli tamsayı giriş parametresine (A ve B) ve bir tamsayı çıkış parametresine (C) sahiptir. Adder görevi iki giriş parametresini ekler ve çıktı parametresinde toplamı döndürür. Toplam, MSBuild olarak `Sum` yayımlar. TestBuild hedefi Adder görevini çağıran giriş parametrelerinin değerleri ayarlanır.

## <a name="define-the-regx-task"></a>RegX görevini tanımlama

 Bir öğe grubu ve normal ifade kabul eden ve ifadeyle eşleşen dosya içeriğine sahip tüm öğelerin listesini döndüren bir satır içi görev oluşturun.

#### <a name="to-define-the-regx-task"></a>RegX görevini tanımlamak için

1. Kod düzenleyicisinde, aşağıdaki kodu kullanarak Adder görevini ve TestBuild hedefini değiştirin.

   ```xml
   <UsingTask TaskName="RegX" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Expression Required="true" />
       <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
       <Result ParameterType="Microsoft.Build.Framework.ITaskItem[]" Output="true" />
     </ParameterGroup>
     <Task>
       <Using Namespace="System.Text.RegularExpressions"/>
       <Code Type="Fragment" Language="cs">
   <![CDATA[
         if (Files.Length > 0)
         {
           Result = new TaskItem[Files.Length];
           for (int i = 0; i < Files.Length; i++)
           {
             ITaskItem item = Files[i];
             string path = item.GetMetadata("FullPath");
             using(StreamReader rdr = File.OpenText(path))
             {
               if (Regex.Match(rdr.ReadToEnd(), Expression).Success)
               {
                 Result[i] = new TaskItem(item.ItemSpec);
               }
             }
           }
         }
   ]]>
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <RegX Expression="public|protected" Files="@(Compile)">
       <Output ItemName="MatchedFiles" TaskParameter="Result" />
     </RegX>
     <Message Text="Input files: @(Compile)" Importance="High" />
     <Message Text="Matched files: @(MatchedFiles)" Importance="High" />
   </Target>
   ```

2. Komut **İstemi Penceresi'ne** komut anahtarları olmadan **msbuild** yazın ve Enter tuşuna **basın.** Varsayılan olarak, bu, RegX görevini çağıran varsayılan hedef TestBuild'i işler.

3. Komut İstemi **Penceresindeki çıktıyı inceleme.** Şu satırları görmeniz gerekir:

   ```
   Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
   ```

   ```
   Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs
   ```

   Bu kod, RegX adlı ve şu üç parametreye sahip olan bir satır içi görevi tanımlar:

- `Expression` , eşleşmesi gereken normal ifade olan bir değere sahip gerekli bir dize giriş parametresidir. Bu örnekte, ifade "public" veya "protected" sözcükleriyle eştir.

- `Files` , eşleşme aranacak dosyaların listesi olan bir değere sahip gerekli bir öğe listesi giriş parametresidir. Bu örnekte, `Files` proje kaynak dosyalarını `Compile` listeleye öğe olarak ayarlanmıştır.

- `Result` , normal ifadeyle eşan içeriklere sahip dosyaların listesi olan bir değere sahip olan bir çıkış parametresidir.

  TestBuild hedefi RegX görevini çağıran giriş parametrelerinin değeri ayarlanır. RegX görevi her dosyayı okur ve normal ifadeyle eş değere sahip dosyaların listesini döndürür. Bu liste, öğesi `Result` olarak yayılan çıkış parametresi olarak MSBuild `MatchedFiles` döndürülür.

### <a name="handle-reserved-characters"></a>Ayrılmış karakterleri işleme

 Veri MSBuild satır içi görevleri XML olarak işler. XML'de ayrılmış anlamı olan karakterler (örneğin, " " ) algılanır ve .NET kaynak kodu değil XML gibi \<" and "> işlanır. gibi kod ifadelerine ayrılmış karakterleri eklemek için, içeriğinin bir CDATA ifadesinde yer alan öğesini `Files.Length > 0` `Code` aşağıdaki gibi yazın:

 ```xml
<Code Type="Fragment" Language="cs">
  <![CDATA[

  if (Files.Length > 0)
  {
      // Your code goes here.
  }
  ]]>
</Code>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Satır içi görevleri](../msbuild/msbuild-inline-tasks.md)
- [Görevler](../msbuild/msbuild-tasks.md)
- [Targets](../msbuild/msbuild-targets.md)
