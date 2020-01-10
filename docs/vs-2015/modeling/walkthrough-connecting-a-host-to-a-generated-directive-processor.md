---
title: 'İzlenecek yol: bir konağı oluşturulan yönerge Işlemcisine bağlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
ms.assetid: 254540d9-90d6-42de-8c1c-068affd56e83
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 47e1b1f11fd885afbb5e84e1530a171442938af0
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851290"
---
# <a name="walkthrough-connecting-a-host-to-a-generated-directive-processor"></a>İzlenecek yol: Üretilen bir Yönerge İşlemcisine Ana Bilgisayar Bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin şablonlarını işleyen kendi ana bilgisayarınızı yazabilirsiniz. [Izlenecek yol: özel metin şablonu Konağı oluşturma](../modeling/walkthrough-creating-a-custom-text-template-host.md)bölümünde temel bir özel ana bilgisayar gösterilmiştir. Birden çok çıktı dosyası oluşturma gibi işlevleri eklemek için bu konağı genişletebilirsiniz.

 Bu kılavuzda, özel ana bilgisayarınızı genişleterek yönerge işlemcileri çağıran metin şablonlarını destekliyor. Alana özgü bir dil tanımladığınızda, etki alanı modeli için bir *yönerge işlemcisi* oluşturulur. Yönerge işlemcisi, kullanıcıların modele erişen şablonlar yazmasını kolaylaştırır ve bu da şablonlarda derleme ve içeri aktarma yönergeleri yazma ihtiyacını azaltır.

> [!WARNING]
> Bu kılavuzda [Izlenecek yol: özel metin şablonu ana bilgisayarı oluşturma](../modeling/walkthrough-creating-a-custom-text-template-host.md). Önce bu yönergeyi gerçekleştirin.

 Bu izlenecek yol aşağıdaki görevleri içerir:

- Bir etki alanı modelini temel alan bir yönerge işlemcisi oluşturmak için [!INCLUDE[dsl](../includes/dsl-md.md)] kullanma.

- Özel metin şablonu konağını oluşturulan yönerge işlemcisine bağlama.

- Özel ana bilgisayarı oluşturulan yönerge işlemcisi ile test etme.

## <a name="prerequisites"></a>Prerequisites
 Bir DSL tanımlamak için aşağıdaki bileşenler yüklemiş olmanız gerekir:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](https://docs.microsoft.com/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|{1&gt;{2&gt;Visual Studio Görselleştirme ve Modelleme SDK'sı&lt;2}&lt;1}|[http://go.microsoft.com/fwlink/?LinkID=186128](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples)|

 Ayrıca, [Izlenecek yol: özel metin şablonu Konağı oluşturma](../modeling/walkthrough-creating-a-custom-text-template-host.md)bölümünde özel metin şablonu dönüşümünün oluşturulmuş olması gerekir.

## <a name="using-domain-specific-language-tools-to-generate-a-directive-processor"></a>Yönerge Işlemcisi oluşturmak için Alana Özgü Dil Araçları kullanma
 Bu kılavuzda, DSLMinimalTest çözümü için etki alanına özgü bir dil oluşturmak üzere Alana Özgü Dil Tasarımcısı Sihirbazı 'nı kullanırsınız.

#### <a name="to-use-domain-specific-language-tools-to-generate-a-directive-processor-that-is-based-on-a-domain-model"></a>Bir etki alanı modeline dayalı bir yönerge işlemcisi oluşturmak için Alana Özgü Dil Araçları kullanmak için

1. Aşağıdaki özelliklere sahip, etki alanına özgü bir dil çözümü oluşturun:

   - Ad: DSLMinimalTest

   - Çözüm şablonu: minimal dil

   - Dosya Uzantısı: dk

   - Şirket adı: fabrikam

     Etki alanına özgü dil çözümü oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: etki alanına özgü dil çözümü oluşturma](../modeling/how-to-create-a-domain-specific-language-solution.md).

2. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.

   > [!IMPORTANT]
   > Bu adım yönerge işlemcisini oluşturur ve anahtar kayıt defterine ekler.

3. Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat**.

    İkinci bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] örneği açılır.

4. Deneysel derlemede, **Çözüm Gezgini**' de, **Sample. min**dosyasına çift tıklayın.

    Dosya tasarımcıda açılır. Modelin iki öğesi olduğunu, ExampleElement1 ve ExampleElement2 ve aralarında bir bağlantı olduğunu unutmayın.

5. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ikinci örneğini kapatın.

6. Çözümü kaydedin ve sonra Alana Özgü Dil Tasarımcısı kapatın.

## <a name="connecting-a-custom-text-template-host-to-a-directive-processor"></a>Özel metin şablonu konağını yönerge Işlemcisine bağlama
 Yönerge işlemcisini oluşturduktan sonra yönerge işlemcisini ve [Izlenecek yol: özel](../modeling/walkthrough-creating-a-custom-text-template-host.md)metin şablonu ana bilgisayarı oluşturma bölümünde oluşturduğunuz özel metin şablonu konağını bağlanırsınız.

#### <a name="to-connect-a-custom-text-template-host-to-the-generated-directive-processor"></a>Özel bir metin şablonu konağını oluşturulan yönerge işlemcisine bağlamak için

1. CustomHost çözümünü açın.

2. **Proje** menüsünde, **Başvuru Ekle**' ye tıklayın.

     **.Net** sekmesi görüntülenirken **Başvuru Ekle** iletişim kutusu açılır.

3. Aşağıdaki başvuruları ekleyin:

    - Microsoft.VisualStudio.Modeling.Sdk.11.0

    - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

    - Microsoft.VisualStudio.TextTemplating.11.0

    - Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

    - Microsoft.VisualStudio.TextTemplating.VSHost.11.0

4. Program.cs veya Module1. vb 'nin en üstünde aşağıdaki kod satırını ekleyin:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. `StandardAssemblyReferences`özelliği için kodu bulun ve aşağıdaki kodla değiştirin:

    > [!NOTE]
    > Bu adımda, konağın destekleyeceği oluşturulan yönerge işlemcisinin gerektirdiği derlemelere başvurular eklersiniz.

    ```csharp
    //the host can provide standard assembly references
    //the engine will use these references when compiling and
    //executing the generated transformation class
    //--------------------------------------------------------------
    public IList<string> StandardAssemblyReferences
    {
        get
        {
            return new string[]
            {
                //if this host searches standard paths and the GAC
                //we can specify the assembly name like this:
                //"System"
                //since this host only resolves assemblies from the
                //fully qualified path and name of the assembly
                //this is a quick way to get the code to give us the
                //fully qualified path and name of the System assembly
                //---------------------------------------------------------
                typeof(System.Uri).Assembly.Location,
                            typeof(System.Uri).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location

            };
        }
    }
    ```

6. `ResolveDirectiveProcessor`işlev için kodu bulun ve aşağıdaki kodla değiştirin:

    > [!IMPORTANT]
    > Bu kod, bağlanmak istediğiniz oluşturulan yönerge işlemcisinin adına sabit kodlanmış başvurular içerir. Bu durumda kolayca daha genel hale getirebilirsiniz. Bu durumda, kayıt defterinde listelenen tüm yönerge işlemcilerini arar ve bir eşleşme bulmaya çalışır. Bu durumda, ana bilgisayar oluşturulan tüm yönerge işlemcilerle çalışır.

    ```csharp
    //the engine calls this method based on the directives the user has
            //specified it in the text template
            //this method can be called 0, 1, or more times
            //---------------------------------------------------------------------
            public Type ResolveDirectiveProcessor(string processorName)
            {
                //check the processor name, and if it is the name of the processor the
                //host wants to support, return the type of the processor
                //---------------------------------------------------------------------
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)
                {
                    try
                    {
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))
                        {
                            if (specificKey != null)
                            {
                                List<string> names = new List<String>(specificKey.GetValueNames());
                                string classValue = specificKey.GetValue("Class") as string;
                                if (!string.IsNullOrEmpty(classValue))
                                {
                                    string loadValue = string.Empty;
                                    System.Reflection.Assembly processorAssembly = null;
                                    if (names.Contains("Assembly"))
                                    {
                                        loadValue = specificKey.GetValue("Assembly") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //the assembly must be installed in the GAC
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);
                                        }
                                    }
                                    else if (names.Contains("CodeBase"))
                                    {
                                        loadValue = specificKey.GetValue("CodeBase") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //loading local assembly
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);
                                        }
                                    }
                                    if (processorAssembly == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    Type processorType = processorAssembly.GetType(classValue);
                                    if (processorType == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    return processorType;
                                }
                            }
                        }
                    }
                    catch (Exception e)
                    {
                        //if the directive processor can not be found, throw an error
                        throw new Exception("Directive Processor not found");
                    }
                }

                //if the directive processor is not one this host wants to support
                throw new Exception("Directive Processor not supported");
            }
    ```

7. Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet**.

8. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.

## <a name="testing-the-custom-host-with-the-directive-processor"></a>Özel Konağı yönerge Işlemcisi ile test etme
 Özel metin şablonu konağını test etmek için, önce oluşturulan yönerge işlemcisini çağıran bir metin şablonu yazmanız gerekir. Ardından Özel Konağı çalıştırın, metin şablonunun adını geçirin ve yönergesinin doğru şekilde işlendiğini doğrulayın.

#### <a name="to-create-a-text-template-to-test-the-custom-host"></a>Özel ana bilgisayarı sınamak amacıyla metin şablonu oluşturmak için

1. Bir metin dosyası oluşturun ve `TestTemplateWithDP.tt`adlandırın. Dosyayı oluşturmak için Not Defteri gibi herhangi bir metin düzenleyicisini kullanabilirsiniz.

2. Aşağıdakileri metin dosyasına ekleyin:

    > [!NOTE]
    > Metin şablonunun programlama dilinin özel ana bilgisayarla eşleşmesi gerekmez.

    ```csharp
    Text Template Host Test

    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
    <# //this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>
    <# //uncomment this line to test that the host allows the engine to set the extension #>
    <# //@ output extension=".htm" #>

    <# //uncomment this line if you want to see the generated transformation class #>
    <# //System.Diagnostics.Debugger.Break(); #>
    <# //this code uses the results of the examplemodel directive #>
    <#
        foreach ( ExampleElement box in this.ExampleModel.Elements )
        {
            WriteLine("Box: {0}", box.Name);

            foreach (ExampleElement linkedTo in box.Targets)
            {
                WriteLine("Linked to: {0}", linkedTo.Name);
            }

            foreach (ExampleElement linkedFrom in box.Sources)
            {
                WriteLine("Linked from: {0}", linkedFrom.Name);
            }

            WriteLine("");
        }
    #>
    ```

    ```vb
    Text Template Host Test

    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>

    <# 'this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>

    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>
    <# '@ output extension=".htm" #>

    <# 'Uncomment this line if you want to see the generated transformation class. #>
    <# 'System.Diagnostics.Debugger.Break() #>

    <# 'this code uses the results of the examplemodel directive #>

    <#
       For Each box as ExampleElement In Me.ExampleModel.Elements

           WriteLine("Box: {0}", box.Name)

            For Each LinkedTo as ExampleElement In box.Targets
                WriteLine("Linked to: {0}", LinkedTo.Name)
            Next

            For Each LinkedFrom as ExampleElement In box.Sources
                WriteLine("Linked from: {0}", LinkedFrom.Name)
            Next

            WriteLine("")

       Next
    #>
    ```

3. Kodda, yol > \<, ilk yordamda oluşturduğunuz tasarıma özgü dilden Sample. min dosyasının yoluyla değiştirin.

4. Dosyayı kaydedin ve kapatın.

#### <a name="to-test-the-custom-host"></a>Özel ana bilgisayarı sınamak için

1. Bir Komut İstemi penceresi açın.

2. Özel ana bilgisayar için yürütülebilir dosyanın yolunu yazın, ancak henüz ENTER'a basmayın.

     Örneğin, şunu yazın:

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > Adresi yazmak yerine, **Windows Gezgini**'Nde CustomHost. exe dosyasına gidip dosyayı komut istemi penceresine sürükleyebilirsiniz.

3. Bir boşluk yazın.

4. Metin şablonu dosyasının yolunu yazın ve ENTER tuşuna basın.

     Örneğin, şunu yazın:

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > Adresi yazmak yerine, **Windows Gezgini**'Nde TestTemplateWithDP. txt dosyasına gidebilir ve sonra dosyayı komut istemi penceresine sürükleyebilirsiniz.

     Özel ana bilgisayar uygulaması çalışır ve metin şablonu dönüştürme işlemini başlatır.

5. **Windows Gezgini**'Nde, TestTemplateWithDP. txt dosyasını içeren klasöre gidin.

     Klasör, TestTemplateWithDP1. txt dosyasını da içerir.

6. Metin şablonu dönüştürme sonuçlarını görmek için bu dosyayı açın.

     Oluşturulan metin çıktısının sonuçları görüntülenir ve şöyle görünmelidir:

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>Ayrıca Bkz.
 [İzlenecek yol: Özel Metin Şablonu Konağı Oluşturma](../modeling/walkthrough-creating-a-custom-text-template-host.md)
