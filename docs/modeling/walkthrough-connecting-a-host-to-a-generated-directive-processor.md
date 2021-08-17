---
title: Bağlan yönerge işlemcisine konak oluşturma
description: Yönerge işlemcilerini çağıran metin şablonlarını destekleyecek şekilde özel ana bilgisayarını nasıl genişletebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
dev_langs:
- CSharp
- VB
ms.openlocfilehash: d60a7bd348bba51009bbab5264fa94d5370ac4246345e283f51eff72eaf3258a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121443873"
---
# <a name="walkthrough-connect-a-host-to-a-generated-directive-processor"></a>İzlenecek yol: Konağı Oluşturulan bir Yönerge İşlemcisine Bağlama

Metin şablonlarını işen kendi ana bilgisayarını yazabilirsiniz. Temel bir özel konak, [Kılavuz: Özel Metin Şablonu Ana Bilgisayarı Oluşturma konusunda gösterildi.](../modeling/walkthrough-creating-a-custom-text-template-host.md) Birden çok çıkış dosyası oluşturma gibi işlevleri eklemek için bu ana bilgisayarı genişletebilirsiniz.

Bu kılavuzda, yönerge işlemcilerini çağıran metin şablonlarını destekleyecek şekilde özel ana bilgisayarını genişletebilirsiniz. Etki alanına özgü bir dil tanımladığınız zaman, etki alanı modeli *için bir* yönerge işlemcisi üretir. Yönerge işlemcisi, kullanıcıların modele erişen şablonlar yazmalarını kolaylaştırarak şablonlarda derleme ve içeri aktarma yönergeleri yazma ihtiyacının azaltılmasını sağlar.

> [!NOTE]
> Bu izlenecek yol, [Kılavuz: Özel Metin Şablonu Ana Bilgisayarı Oluşturma üzerine oluşturulur.](../modeling/walkthrough-creating-a-custom-text-template-host.md) Önce bu izlenecek yolu gerçekleştirin.

Bu izlenecek yol aşağıdaki görevleri içerir:

- bir [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] etki alanı modelini temel alan bir yönerge işlemcisi oluşturmak için kullanma.

- Özel bir metin şablonu ana bilgisayar tarafından oluşturulan yönerge işlemcisine bağlanma.

- Özel ana bilgisayarı oluşturulan yönerge işlemcisi ile test etme.

## <a name="prerequisites"></a>Önkoşullar

DSL tanımlamak için aşağıdaki bileşenleri yüklemiş olması gerekir:

| Bileşen | Bağlantı |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| Visual Studio Görselleştirme ve Modelleme SDK'sı | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Ayrıca, Özel Metin Şablonu Ana Bilgisayarı Oluşturma adımlarında özel metin şablonu [dönüştürmesi oluşturulmuş olması gerekir.](../modeling/walkthrough-creating-a-custom-text-template-host.md)

## <a name="use-domain-specific-language-tools-to-generate-a-directive-processor"></a>Yönerge Domain-Specific Oluşturmak için Domain-Specific Dil Araçlarını Kullanma

Bu kılavuzda, DSLMinimalTest Domain-Specific etki alanına özgü bir dil oluşturmak için Dil Tasarımcısı Sihirbazı'nı kullanırsınız.

1. Aşağıdaki özelliklere sahip etki alanına özgü bir dil çözümü oluşturun:

   - Ad: DSLMinimalTest

   - Çözüm şablonu: Minimum Dil

   - Dosya uzantısı: dk

   - Şirket adı: Fabrikam

   Etki alanına özgü bir dil çözümü oluşturma hakkında daha fazla bilgi için [bkz. Nasıl: Domain-Specific Dil Çözümü Oluşturma.](../modeling/how-to-create-a-domain-specific-language-solution.md)

2. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

   > [!IMPORTANT]
   > Bu adım yönerge işlemcisini oluşturur ve anahtarı kayıt defterine ekler.

3. **Hata ayıkla** menüsünde **Hata Ayıklamayı Başlat**’a tıklayın.

    İkinci bir örnek Visual Studio açılır.

4. Deneysel derlemede, **Çözüm Gezgini** **sample.min** dosyasına çift tıklayın.

    Dosya tasarımcıda açılır. Modelde Iki öğe (ExampleElement1 ve ExampleElement2) ve aralarında bir bağlantı olduğunu fark edin.

5. uygulamanın ikinci örneğini Visual Studio.

6. Çözümü kaydedin ve ardından Dil Tasarımcısı'Domain-Specific kapatın.

## <a name="connect-a-custom-text-template-host-to-a-directive-processor"></a>Bağlan Bir Yönerge İşlemcisine Özel Metin Şablonu Ana Bilgisayarı Ekleme

Yönerge işlemcisini oluşturduktan sonra yönerge işlemcisini ve Izlenecek Yol: Özel Metin Şablonu Ana Bilgisayarı Oluşturma içinde oluşturduğunuz özel metin şablonu ana [bilgisayarlarını birbirine bağlayabilirsiniz.](../modeling/walkthrough-creating-a-custom-text-template-host.md)

1. CustomHost çözümünü açın.

2. Giriş **menüsünde, Project** **Ekle'ye tıklayın.**

     Başvuru **Ekle iletişim** kutusu açılır ve **.NET sekmesi** görüntülenir.

3. Aşağıdaki başvuruları ekleyin:

    - Microsoft.VisualStudio.Modeling.Sdk.11.0

    - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

    - Microsoft.VisualStudio.TextTemplating.11.0

    - Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

    - Microsoft.VisualStudio.TextTemplating.VSHost.11.0

4. Program.cs veya Module1.vb'nin en üstüne aşağıdaki kod satırı ekleyin:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. özelliğinin kodunu bulun `StandardAssemblyReferences` ve aşağıdaki kodla değiştirin:

    > [!NOTE]
    > Bu adımda, konak tarafından desteklenen oluşturulan yönerge işlemcisi için gereken derlemelere başvurular eklersiniz.

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

6. işlevinin kodunu bulun `ResolveDirectiveProcessor` ve aşağıdaki kodla değiştirin:

    > [!IMPORTANT]
    > Bu kod, bağlanmak istediğiniz oluşturulan yönerge işlemcisinin adına sabit kodlu başvurular içerir. Bu durumu kolayca daha genel hale ebilirsiniz. Bu durumda kayıt defterinde listelenen tüm yönerge işlemcilerini bulup bir eşleşme bulmaya çalışır. Bu durumda, konak oluşturulan herhangi bir yönerge işlemcisi ile çalışır.

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

7. **Dosya** menüsünde **Tümünü Kaydet**’e tıklayın.

8. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

## <a name="test-the-custom-host-with-the-directive-processor"></a>Özel Ana Bilgisayarı Yönerge İşlemcisi ile Test

Özel metin şablonu ana bilgisayarlarını test etmek için önce oluşturulan yönerge işlemcisini çağıran bir metin şablonu yazmanız gerekir. Ardından özel ana bilgisayarı çalıştıracak, buna metin şablonunun adını geçecek ve yönergenin doğru şekilde işlendiğinden emin olun.

### <a name="create-a-text-template-to-test-the-custom-host"></a>Özel ana bilgisayarı test etmek için metin şablonu oluşturma

1. Bir metin dosyası oluşturun ve olarak ad `TestTemplateWithDP.tt` girin. Dosyayı oluşturmak için Not Defteri gibi herhangi bir metin düzenleyicisini kullanabilirsiniz.

2. Aşağıdakileri metin dosyasına ekleyin:

    > [!NOTE]
    > Metin şablonunun programlama dilinin özel ana bilgisayarla eşleşmesi gerekir.

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

3. Kodda yerine ilk yordamda oluşturduğunuz tasarıma özgü \<YOUR PATH> dilden Sample.min dosyasının yolunu girin.

4. Dosyayı kaydedin ve kapatın.

### <a name="test-the-custom-host"></a>Özel ana bilgisayarı test etmek

1. Bir komut istemi penceresi açın.

2. Özel ana bilgisayar için yürütülebilir dosyanın yolunu yazın, ancak henüz ENTER'a basmayın.

     Örneğin, şunu yazın:

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > Adresi yazmak yerine, Windows **Gezgini'nde** CustomHost.exe dosyasına göz atabilir ve ardından dosyayı Komut İstemi penceresine sürükleyebilirsiniz.

3. Bir boşluk yazın.

4. Metin şablonu dosyasının yolunu yazın ve ENTER tuşuna basın.

     Örneğin, şunu yazın:

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > Adresi yazmak yerine, Windows **Gezgini'nde** TestTemplateWithDP.txt dosyasına göz atabilir ve ardından dosyayı Komut İstemi penceresine sürükleyebilirsiniz.

     Özel konak uygulaması çalışır ve metin şablonu dönüştürme işlemini başlatır.

5. **Gezgin Windows de,** dosya adını içeren klasöre TestTemplateWithDP.txt.

     Klasör ayrıca dosya adını da TestTemplateWithDP1.txt.

6. Metin şablonu dönüştürme sonuçlarını görmek için bu dosyayı açın.

     Oluşturulan metin çıkışının sonuçları görüntülenir ve şu şekilde görünür:

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Özel Metin Şablonu Konağı Oluşturma](../modeling/walkthrough-creating-a-custom-text-template-host.md)
