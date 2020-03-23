---
title: 'Walkthrough: Satır Satır Oluşturma | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
- MSBuild, tasks
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70ce19a6dcd9c61b0e14d0d88c52072f59f87fb9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631165"
---
# <a name="walkthrough-create-an-inline-task"></a>Walkthrough: Satır içinde görev oluşturma

MSBuild görevleri genellikle <xref:Microsoft.Build.Framework.ITask> arabirimi uygulayan bir sınıf derleyerek oluşturulur. .NET Framework sürümü 4'ten başlayarak, proje dosyasında sıralı görevler oluşturabilirsiniz. Görevi barındırmak için ayrı bir derleme oluşturmanız gerekmez. Daha fazla bilgi için [Satır İçi görevlere](../msbuild/msbuild-inline-tasks.md)bakın.

 Bu gözden geçirme, bu satır satır görevlerinin nasıl oluşturulup çalıştırılabildiğini gösterir:

- Giriş veya çıkış parametreleri olmayan bir görev.

- Bir giriş parametresi olan ve çıktı parametreleri olmayan bir görev.

- İki giriş parametresi ve MSBuild özelliğidöndüren bir çıkış parametresi olan bir görev.

- İki giriş parametresi ve bir MSBuild öğesi döndüren bir çıkış parametresi olan bir görev.

Görevleri oluşturmak ve çalıştırmak için Visual Studio ve **Visual Studio Komut İstepenceresi'ni**aşağıdaki gibi kullanın:

1. Visual Studio'u kullanarak bir MSBuild proje dosyası oluşturun.

2. Satır arası görevi oluşturmak için Visual Studio'daki proje dosyasını değiştirin.

3. Projeyi oluşturmak ve sonuçları incelemek için **Komut İstemi Penceresini** kullanın.

## <a name="create-and-modify-an-msbuild-project"></a>BIR MSBuild projesi oluşturma ve değiştirme

 Visual Studio proje sistemi MSBuild'i temel alır. Bu nedenle, Visual Studio kullanarak bir yapı proje dosyası oluşturabilirsiniz. Bu bölümde, bir Visual C# proje dosyası oluşturun. (Bunun yerine Visual Basic proje dosyası oluşturabilirsiniz. Bu öğretici bağlamında, iki proje dosyası arasındaki fark küçüktür.)

#### <a name="to-create-and-modify-a-project-file"></a>Proje dosyası oluşturmak ve değiştirmek için

1. Visual Studio'da C# **Windows Forms Application** şablonu kullanarak yeni bir proje oluşturun. **Ad** kutusuna `InlineTasks` yazın. Çözüm için bir **Konum** yazın, örneğin, *D:\\*. Çözüm **için Oluştur dizini** seçildiğinden, **Kaynak Denetimine Ekle'nin** temizlendiğini ve Çözüm **Adı'nın Satır İçi Görevler**olduğundan emin olun. **Solution Name**

3. Proje dosyasını oluşturmak için **Tamam'ı** tıklatın.

3. **Çözüm Gezgini'nde,** **InlineTasks** proje düğüme sağ tıklayın ve ardından **Project'i Boşalt'ı**tıklatın.

4. Proje düğümüne tekrar sağ tıklayın ve ardından **InlineTasks.csproj'u düzenle'yi**tıklatın.

     Proje dosyası kod düzenleyicisinde görüntülenir.

## <a name="add-a-basic-hello-task"></a>Temel bir Merhaba görevi ekleme

 Şimdi, proje dosyasına "Merhaba, dünya!" iletisini görüntüleyen temel bir görev ekleyin. Ayrıca görevi çağırmak için varsayılan bir TestBuild hedefi ekleyin.

#### <a name="to-add-a-basic-hello-task"></a>Temel bir Merhaba görevi eklemek için

1. Kök `Project` düğümde, özniteliği `DefaultTargets` ni `TestBuild`' ye çevirin. Elde edilen `Project` düğüm bu örneğe benzemelidir:

   ```xml
   <Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   ```

2. `</Project>` Etiketten hemen önce proje dosyasına aşağıdaki satır çizgisi görev ve hedefi ekleyin.

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

   Bu kod, Merhaba adlı ve hiçbir parametre, başvuru veya `Using` yönergesi olmayan bir satır dışı görev oluşturur. Merhaba görevi, varsayılan günlük aygıtında genellikle konsol penceresinde bir merhaba iletisi görüntüleyen yalnızca bir kod satırı içerir.

### <a name="run-the-hello-task"></a>Merhaba görevini çalıştırın

 Merhaba görevini oluşturmak ve onu çağıran TestBuild hedefini işlemek için **Komut İstemi Penceresini** kullanarak MSBuild'i çalıştırın.

##### <a name="to-run-the-hello-task"></a>Merhaba görevini çalıştırmak için

1. **Başlat'ı**tıklatın, **Tüm Programlar'ı**tıklatın ve ardından **Visual Studio Tools** klasörünü bulun ve Visual Studio Komut Komut **Istemi'ni**tıklatın.

2. Komut **İstemi Penceresinde,** proje dosyasını içeren klasörü bulun, bu durumda, *D:\InlineTasks\InlineTasks\\*.

3. Komut anahtarları olmadan **msbuild** yazın ve sonra **Enter**tuşuna basın. Varsayılan olarak, bu *InlineTasks.csproj* dosyasını oluşturur ve Merhaba görevini çağıran varsayılan hedef TestBuild'i işler.

4. **Komut İstem Penceresindeki**çıktıyı inceleyin. Şu satırı görmeniz gerekir:

    `Hello, world!`

   > [!NOTE]
   > Merhaba iletisini görmüyorsanız, proje dosyasını yeniden kaydetmeyi deneyin ve ardından Merhaba görevini çalıştırın.

   Kod düzenleyicisi ve **Komut İstem Penceresi**arasında dönüşümlü olarak, proje dosyasını değiştirebilir ve sonuçları hızlı bir şekilde görebilirsiniz.

## <a name="define-the-echo-task"></a>Yankı görevini tanımlama

 Dize parametresini kabul eden ve varsayılan günlük aygıtında dizeyi görüntüleyen satır içinde bir görev oluşturun.

#### <a name="to-define-the-echo-task"></a>Yankı görevini tanımlamak için

1. Kod düzenleyicisinde, aşağıdaki kodu kullanarak Hello görev ve TestBuild hedefini değiştirin.

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

2. Komut **İstemi Penceresinde,** komut anahtarları olmadan **msbuild** yazın ve sonra **Enter**tuşuna basın. Varsayılan olarak, bu, Yankı görevini çağıran varsayılan hedef TestBuild'i işler.

3. **Komut İstem Penceresindeki**çıktıyı inceleyin. Şu satırı görmeniz gerekir:

    `Greetings!`

   Bu kod, Yankı adlı bir satır içinde görev tanımlar ve yalnızca bir gerekli giriş parametresi Metin vardır. Varsayılan olarak, parametreler System.String türündendir. TestBuild hedefi Yankı görevini çağırdığında Metin parametresinin değeri ayarlanır.

## <a name="define-the-adder-task"></a>Toplayıcı görevini tanımlama

 İki karşıcı parametre ekleyen ve toplamlarını MSBuild özelliği olarak yakan satır dışı bir görev oluşturun.

#### <a name="to-define-the-adder-task"></a>Adder görevini tanımlamak için

1. Kod düzenleyicisinde, aşağıdaki kodu kullanarak Yankı görevi ve TestBuild hedefini değiştirin.

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

2. Komut **İstemi Penceresinde,** komut anahtarları olmadan **msbuild** yazın ve sonra **Enter**tuşuna basın. Varsayılan olarak, bu, Yankı görevini çağıran varsayılan hedef TestBuild'i işler.

3. **Komut İstem Penceresindeki**çıktıyı inceleyin. Şu satırı görmeniz gerekir:

    `The sum is 9`

   Bu kod, Adder adlı bir satır altı görevi tanımlar ve iki gerekli tamsayı giriş parametresi, A ve B ve bir tamsayı çıkış parametresi, C vardır. Adder görevi iki giriş parametresini ekler ve çıktı parametresinde toplamı döndürür. Toplam, MSBuild özelliği `Sum`olarak yayılır. TestBuild hedefi Adder görevini çağırdığında giriş parametrelerinin değerleri ayarlanır.

## <a name="define-the-regx-task"></a>RegX görevini tanımlama

 Madde grubunu ve normal bir ifadeyi kabul eden ve ifadeyle eşleşen dosya içeriğine sahip tüm öğelerin listesini döndüren satır dışı bir görev oluşturun.

#### <a name="to-define-the-regx-task"></a>RegX görevini tanımlamak için

1. Kod düzenleyicisinde, aşağıdaki kodu kullanarak Adder görev ve TestBuild hedefini değiştirin.

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

2. Komut **İstemi Penceresinde,** komut anahtarları olmadan **msbuild** yazın ve sonra **Enter**tuşuna basın. Varsayılan olarak, bu regx görev çağırır varsayılan hedef TestBuild, işler.

3. **Komut İstem Penceresindeki**çıktıyı inceleyin. Şu satırları görmeniz gerekir:

   ```
   Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
   ```

   ```
   Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs
   ```

   Bu kod, RegX adlı bir satır dışı görev tanımlar ve şu üç parametreye sahiptir:

- `Expression`eşleşmesi gereken normal ifade değeri olan gerekli bir dize giriş parametresidir. Bu örnekte, ifade "genel" veya "korumalı" sözcükleri ile eşleşir.

- `Files`eşleşme için aranacak dosyaların listesi olan bir değere sahip gerekli madde listesi giriş parametresidir. Bu örnekte, `Files` proje `Compile` kaynak dosyalarını listeleyen öğeye ayarlanır.

- `Result`normal ifadeyle eşleşen içeriği olan dosyaların listesi olan bir değere sahip bir çıktı parametresitir.

  TestBuild hedefi RegX görevini çağırdığında giriş parametrelerinin değeri ayarlanır. RegX görevi her dosyayı okur ve normal ifadeyle eşleşen dosyaların listesini döndürür. Bu liste, MSBuild öğesi `Result` `MatchedFiles`olarak yayılan çıktı parametresi olarak döndürülür.

### <a name="handle-reserved-characters"></a>Ayrılmış karakterleri işleme

 MSBuild parser satır sıralı görevleri XML olarak işler. XML'de anlamı saklı olan karakterler\<, örneğin " " ve ">", .NET kaynak kodu değil, XML gibi algılanır ve işlenir. Ayrılmış karakterleri kod ifadelerine eklemek `Files.Length > 0`için, öğeyi aşağıdaki gibi bir CDATA ifadesinde içerecek şekilde yazın: `Code`

 ```xml
<Code Type="Fragment" Language="cs">
  <![CDATA[

  // Your code goes here.

  ]]>
</Code>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Satır İçi görevler](../msbuild/msbuild-inline-tasks.md)
- [Görevler](../msbuild/msbuild-tasks.md)
- [Hedef](../msbuild/msbuild-targets.md)
