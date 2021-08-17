---
title: 'Nasıl Yapılır: Sihirbazları Proje Şablonlarıyla Kullanma'
description: bir kullanıcı şablondan bir proje oluşturduğunda özel kod çalıştırmanızı sağlayan Visual Studio SDK 'sında ıwizard arabirimini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: cc023655c42ea63db5015d00a33ce140275f6ee0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095068"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Nasıl yapılır: Sihirbazları Proje Şablonlarıyla Kullanma

Visual Studio, <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> uygulandığında bir kullanıcı şablondan bir proje oluşturduğunda özel kod çalıştırmanızı sağlayan arayüzü sağlar.

Project şablon özelleştirmesi, şablonu özelleştirmek, şablona başka dosyalar eklemek veya bir projede izin verilen başka bir eyleme kullanıcı girişi toplayan özel kullanıcı arabirimini göstermek için kullanılabilir.

<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>arabirim yöntemleri, bir kullanıcı **yeni Project** iletişim kutusunda **tamam** ' a tıkladıktan hemen sonra, proje oluşturulurken çeşitli zamanlarda çağrılır. Arabirimin her yöntemi, çağrıldığı noktayı açıklayan şekilde adlandırılır. örneğin, Visual Studio, <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> projeyi oluşturmaya başladığında hemen çağırır ve bu, kullanıcı girişini toplamak için özel kod yazmak üzere iyi bir konum yapar.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>VSıX projesiyle proje şablonu projesi oluşturma

proje şablonu projesi ile Visual Studio SDK 'sının bir parçası olan özel bir şablon oluşturmaya başlayabilirsiniz. bu yordamda, bir C# proje şablonu projesi kullanacağız, ancak aynı zamanda bir Visual Basic proje şablonu projesi de vardır. Ardından, proje şablonu projesini içeren çözüme bir VSıX projesi eklersiniz.

1. bir C# proje şablonu projesi oluşturun (Visual Studio, **dosya**  >  **yeni**  >  **Project** seçin ve "proje şablonu" araması yapın. **Myprojecttemplate** olarak adlandırın.

   > [!NOTE]
   > Visual Studio SDK 'yı yüklemek isteyip istemediğiniz sorulabilir. daha fazla bilgi için bkz. [Visual Studio SDK 'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).

2. proje şablonu projesiyle aynı çözüme yeni bir vsıx projesi ekleyin ( **Çözüm Gezgini**, çözüm düğümünü seçin, sağ tıklayın ve yeni Project **ekle**' yi seçin  >   ve "vsıx" araması yapın). **Myprojectwizard** olarak adlandırın.

3. VSıX projesini başlangıç projesi olarak ayarlayın. **Çözüm Gezgini**, VSIX projesi düğümünü seçin, sağ tıklayın ve **Başlangıç Project olarak ayarla**' yı seçin.

4. Şablon projesini VSıX projesinin bir varlığı olarak ekleyin. **Çözüm Gezgini**, VSIX projesi düğümünün altında *Source. Extension. valtmanifest* dosyasını bulun. Bildirim düzenleyicisinde açmak için çift tıklayın.

5. Bildirim düzenleyicisinde pencerenin sol tarafındaki **varlıklar** sekmesini seçin.

6. **Varlıklar** sekmesinde **Yeni**' yi seçin. **Yeni varlık Ekle** penceresinde tür alanı için **Microsoft. VisualStudio. ProjectTemplate**' i seçin. **Kaynak** alanında, **Geçerli çözümde bir proje** seçin. **Project** alanında **myprojecttemplate**' i seçin. Daha sonra, **Tamam**'a tıklayın.

7. Çözümü oluşturun ve hata ayıklamayı başlatın. ikinci bir Visual Studio örneği görüntülenir. (Bu işlem birkaç dakika sürebilir.)

8. Visual Studio ikinci örneğinde yeni şablonunuz ile yeni bir proje oluşturmayı deneyin (**dosya**  >  **yeni**  >  **Project**, "myproject" araması yapın). Yeni proje **Class1** adlı bir sınıfla görüntülenmelidir. Artık özel bir proje şablonu oluşturdunuz! Hata ayıklamayı Şimdi durdur.

## <a name="create-a-custom-template-wizard"></a>Özel Şablon Sihirbazı oluşturma

bu yordamda, proje oluşturulmadan önce Windows formu açan özel bir sihirbazın nasıl oluşturulacağı gösterilmektedir. Form, kullanıcıların proje oluşturma sırasında kaynak koda eklenen özel bir parametre değeri eklemesine olanak tanır.

1. Bir derleme oluşturmasına izin vermek için VSıX projesini ayarlayın.

2. **Çözüm Gezgini**, VSIX projesi düğümünü seçin. **Çözüm Gezgini**, **Özellikler** penceresini görmeniz gerekir. Bunu yapmazsanız, özellikleri **görüntüle**  >  **penceresini** seçin veya **F4** tuşuna basın. **Özellikler** penceresinde aşağıdaki alanları seçin `true` :

   - **Derlemeyi VSıX kapsayıcısına Ekle**

   - **VSıX kapsayıcısına hata ayıklama sembolleri dahil et**

   - **Yerel VSıX dağıtımında hata ayıklama sembolleri Ekle**

3. Derlemeyi VSıX projesine varlık olarak ekleyin. *Source. Extension. valtmanifest* dosyasını açın ve **varlıklar** sekmesini seçin. **yeni varlık ekle** penceresinde, **tür** için **Microsoft. VisualStudio. Assembly**' i seçin, **kaynak** için **geçerli çözümde bir proje** seçin ve **Project** **myprojectwizard** öğesini seçin.

4. Aşağıdaki başvuruları VSıX projesine ekleyin. ( **Çözüm Gezgini**, VSIX projesi düğümünün altında, **Başvurular**' ı seçin, sağ tıklayın ve **Başvuru Ekle**' yi seçin.) **başvuru ekle** iletişim kutusunda, **Framework** sekmesinde **System. Windows Forms** derlemesini bulun ve seçin. Ayrıca, **System** ve **System. Drawing** derlemelerini bulun ve seçin. Şimdi **Uzantılar** sekmesini seçin. **EnvDTE** derlemesini bulun ve seçin. Ayrıca **Microsoft. VisualStudio. TemplateWizardInterface** derlemesini bulun ve seçin. **Tamam**'a tıklayın.

5. VSıX projesine sihirbaz uygulamasına yönelik bir sınıf ekleyin. ( **Çözüm Gezgini**, VSIX proje düğümüne sağ tıklayın ve **Ekle**' yi ve ardından **Yeni öğe**' yi ve ardından **sınıf**' ı seçin.) Sınıfı **Wizardimplementation** olarak adlandırın.

6. *Wizardimplementationclass. cs* dosyasındaki kodu aşağıdaki kodla değiştirin:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.TemplateWizard;
   using System.Windows.Forms;
   using EnvDTE;

   namespace MyProjectWizard
   {
       public class WizardImplementation:IWizard
       {
           private UserInputForm inputForm;
           private string customMessage;

           // This method is called before opening any item that
           // has the OpenInEditor attribute.
           public void BeforeOpeningFile(ProjectItem projectItem)
           {
           }

           public void ProjectFinishedGenerating(Project project)
           {
           }

           // This method is only called for item templates,
           // not for project templates.
           public void ProjectItemFinishedGenerating(ProjectItem
               projectItem)
           {
           }

           // This method is called after the project is created.
           public void RunFinished()
           {
           }

           public void RunStarted(object automationObject,
               Dictionary<string, string> replacementsDictionary,
               WizardRunKind runKind, object[] customParams)
           {
               try
               {
                   // Display a form to the user. The form collects
                   // input for the custom message.
                   inputForm = new UserInputForm();
                   inputForm.ShowDialog();

                   customMessage = UserInputForm.CustomMessage;

                   // Add custom parameters.
                   replacementsDictionary.Add("$custommessage$",
                       customMessage);
               }
               catch (Exception ex)
               {
                   MessageBox.Show(ex.ToString());
               }
           }

           // This method is only called for item templates,
           // not for project templates.
           public bool ShouldAddProjectItem(string filePath)
           {
               return true;
           }
       }
   }
   ```

    Bu kodda başvurulan **UserInputForm** daha sonra uygulanacak.

    `WizardImplementation`Sınıfı, öğesinin her üyesinin yöntem uygulamalarını içerir <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> . Bu örnekte, yalnızca <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> yöntemi bir görev gerçekleştirir. Diğer tüm yöntemler hiçbir şey yapmaz ya da döndürmez `true` .

    <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>Yöntemi dört parametre kabul eder:

   - <xref:System.Object> <xref:EnvDTE._DTE> Projeyi özelleştirmenizi sağlamak için kök nesnesine bir tür parametresi.

   - <xref:System.Collections.Generic.Dictionary%602>Şablondaki önceden tanımlanmış tüm parametrelerin koleksiyonunu içeren bir parametre. Şablon parametreleri hakkında daha fazla bilgi için bkz. [şablon parametreleri](../ide/template-parameters.md).

   - <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind>Ne tür bir şablon kullanıldığı hakkında bilgi içeren bir parametre.

   - <xref:System.Object>Visual Studio tarafından sihirbaza geçirilmiş bir parametre kümesi içeren bir dizi.

     Bu örnek, Kullanıcı giriş formundan parametresine bir parametre değeri ekler <xref:System.Collections.Generic.Dictionary%602> . Projedeki parametrenin her örneği, `$custommessage$` Kullanıcı tarafından girilen metinle birlikte değişir.

7. Şimdi **UserInputForm**'u oluşturun. *Wizardimplementation. cs* dosyasında, sınıfının sonundan sonra aşağıdaki kodu ekleyin `WizardImplementation` .

   ```csharp
   public partial class UserInputForm : Form
       {
           private static string customMessage;
           private TextBox textBox1;
           private Button button1;

           public UserInputForm()
           {
               this.Size = new System.Drawing.Size(155, 265);

               button1 = new Button();
               button1.Location = new System.Drawing.Point(90, 25);
               button1.Size = new System.Drawing.Size(50, 25);
               button1.Click += button1_Click;
               this.Controls.Add(button1);

               textBox1 = new TextBox();
               textBox1.Location = new System.Drawing.Point(10, 25);
               textBox1.Size = new System.Drawing.Size(70, 20);
               this.Controls.Add(textBox1);
           }
           public static string CustomMessage
           {
               get
               {
                   return customMessage;
               }
               set
               {
                   customMessage = value;
               }
           }
           private void button1_Click(object sender, EventArgs e)
           {
               customMessage = textBox1.Text;
               this.Close();
           }
       }
   ```

    Kullanıcı giriş formu, özel bir parametre girmek için basit bir form sağlar. Form adlı bir metin kutusu `textBox1` ve adlı bir düğme içerir `button1` . Düğmeye tıklandığında, metin kutusundaki metin `customMessage` parametresinde depolanır.

## <a name="connect-the-wizard-to-the-custom-template"></a>sihirbazı özel şablona Bağlan

Özel proje şablonunuzun özel Sihirbazı kullanması için, sihirbaz derlemesini imzalamanız ve yeni bir proje oluşturulduğunda sihirbaz uygulamasının nerede bulabileceğinizi bilmesini sağlamak için özel proje şablonunuza bazı satırlar eklemeniz gerekir.

1. Derlemeyi imzalayın. **Çözüm Gezgini** vsıx projesini seçin, sağ tıklayın ve **Project özellikler**' i seçin.

2. **Project özellikler** penceresinde **imzalama** sekmesini seçin. **imzalama** sekmesinde, **derlemeyi imzala**' yı işaretleyin. **Tanımlayıcı ad seçin anahtar dosyası** alanında öğesini seçin **\<New>** . **Tanımlayıcı ad oluştur anahtar** penceresinde, **anahtar dosya adı** alanına **Key. snk** yazın. **Anahtar dosyamı parola Ile koru** alanı seçimini kaldırın.

3. **Çözüm GEZGINI** VSIX projesi ' ni seçin ve **Özellikler** penceresini bulun.

4. **Derleme çıkışını çıkış dizinine Kopyala** alanını **doğru** olarak ayarlayın. Bu, çözüm yeniden oluşturulduğunda derlemenin çıkış dizinine kopyalanmasını sağlar. Hala dosyada yer alır `.vsix` . İmza anahtarını bulmak için derlemeyi görmeniz gerekir.

5. Çözümü yeniden derleyin.

6. Artık MyProjectWizard proje dizininde (*\<your disk location> \MyProjectTemplate\MyProjectWizard\key.snk*) Key. snk dosyasını bulabilirsiniz. *Key. snk* dosyasını kopyalayın.

7. Çıkış dizinine gidin ve derlemeyi bulun (*\<your disk location> \ myprojecttemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll*). *Key. snk* dosyasını buraya yapıştırın. (Bu kesinlikle gerekli değildir, ancak aşağıdaki adımları daha kolay hale getirir.)

8. Bir komut penceresi açın ve derlemenin oluşturulduğu dizine geçin.

9. *sn.exe* imzalama aracını bulun. örneğin, Windows 10 64 bit işletim sisteminde, tipik bir yol aşağıdaki gibi olacaktır:

     *C:\Program Files (x86) \microsoft sdk 'ları \ Windows \v10.0a\bin\netfx 4.6.1 Tools*

     Aracı bulamıyorsanız komut penceresinde **WHERE/r. sn.exe** çalıştırmayı deneyin. Yolu bir yere unutmayın.

10. *Anahtar. snk* dosyasındaki ortak anahtarı ayıklayın. Komut penceresinde, şunu yazın

     **\<location of sn.exe>\sn.exe-p key. snk çıkışdosyası. Key.**

     Dizin adlarında boşluklar varsa *sn.exe* yolunu tırnak işaretleriyle çevrelemeyi unutmayın!

11. Çıkışınızdan ortak anahtar belirtecini al:

     **\<location of sn.exe>\sn.exe-t çıkışdosyası. Key.**

     Yine, tırnak işaretlerini unutmayın. Çıktıda aşağıdaki gibi bir satır görmeniz gerekir

     **Ortak anahtar belirteci \<token>**

     Bu değeri bir yere getirin.

12. Özel sihirbaza başvuruyu proje şablonunun *. vstemplate* dosyasına ekleyin. **Çözüm Gezgini**, *myprojecttemplate. vstemplate* adlı dosyayı bulun ve açın. Bölümün sonundan sonra \<TemplateContent> aşağıdaki bölümü ekleyin:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Burada **Myprojectwizard** derlemenin adıdır ve **belirteç** , önceki adımda kopyaladığınız belirteçtir.

13. Projedeki tüm dosyaları kaydedin ve yeniden derleyin.

## <a name="add-the-custom-parameter-to-the-template"></a>Şablona özel parametreyi ekleyin

Bu örnekte, şablon olarak kullanılan proje, özel sihirbazın kullanıcı giriş formunda belirtilen iletiyi görüntüler.

1. **Çözüm Gezgini**, **myprojecttemplate** projesine gidin ve *Class1. cs*' yi açın.

2. `Main`Uygulamanın yönteminde aşağıdaki kod satırını ekleyin.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Parametresi, `$custommessage$` şablondan bir proje oluşturulduğunda Kullanıcı giriş formuna girilen metinle değiştirilmiştir.

Bir şablona gönderilmeden önce tam kod dosyası aşağıda verilmiştir.

```csharp
using System;
using System.Collections.Generic;
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;
$endif$using System.Text;

namespace $safeprojectname$
{
    public class Class1
    {
          static void Main(string[] args)
          {
               Console.WriteLine("$custommessage$");
          }
    }
}
```

## <a name="use-the-custom-wizard"></a>Özel Sihirbazı kullanma

Artık, şablonınızdan bir proje oluşturabilir ve özel Sihirbazı kullanabilirsiniz.

1. Çözümü yeniden oluşturun ve hata ayıklamayı başlatın. ikinci bir Visual Studio örneği görünmelidir.

2. Yeni bir MyProjectTemplate projesi oluşturun. (**Dosya**  >  **Yeni**  >  **Project**).

3. **yeni Project** iletişim kutusunda şablonunuzu bulmak için "myproject" araması yapın, bir ad yazın ve **tamam**' a tıklayın.

     Sihirbaz kullanıcı giriş formu açılır.

4. Özel parametre için bir değer yazın ve düğmeye tıklayın.

     Sihirbaz kullanıcı giriş formu kapanır ve şablondan bir proje oluşturulur.

5. **Çözüm Gezgini**, kaynak kodu dosyasına sağ tıklayın ve **kodu görüntüle**' ye tıklayın.

     `$custommessage$`Sihirbazın kullanıcı giriş formuna girilen metinle değiştirildiğini unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [wizardexgeri öğesi (Visual Studio şablonları)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Visual Studio şablonlarındaki NuGet paketleri](/nuget/visual-studio-extensibility/visual-studio-templates)
