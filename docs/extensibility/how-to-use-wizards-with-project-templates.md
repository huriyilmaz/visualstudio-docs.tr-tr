---
title: 'Nasıl Yapılır: Sihirbazları Proje Şablonlarıyla Kullanma'
description: Kullanıcı şablondan proje oluşturduğunda özel kod çalıştırmanızı sağlayan IWizard arabirimini Visual Studio SDK'da kullanmayı öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626240"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Nasıl oluşturulur: Sihirbazları proje şablonlarıyla kullanma

Visual Studio, bir kullanıcı şablondan proje oluşturduğunda özel kod çalıştırmanızı sağlayan <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> arabirimi sağlar.

Project özelleştirme, şablonu özelleştirmek için kullanıcı girişi toplayan özel kullanıcı arabirimini görüntülemek, şablona ek dosya eklemek veya projede izin verilen diğer herhangi bir eylemi görüntülemek için kullanılabilir.

Arabirim yöntemleri proje oluşturulurken çeşitli zamanlarda çağrılır ve kullanıcı Yeni Giriş iletişim kutusunda <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> **Tamam'a Project** olarak başlayarak.  Arabirimin her yöntemi, çağrıldıları noktanın açıklaması için adlandırılmıştır. Örneğin, Visual Studio hemen çağırarak kullanıcı girişini toplamak için özel kod yazmak için iyi bir <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> konum oluşturabilirsiniz.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>VSIX projesiyle proje şablonu projesi oluşturma

Visual Studio SDK'sı kapsamındaki proje şablonu projesiyle özel bir şablon oluşturmaya başlarsınız. Bu yordamda bir C# proje şablonu projesi kullanmayacak ancak proje şablonu projesinde Visual Basic de vardır. Ardından, proje şablonu projesini içeren çözüme bir VSIX projesi eklersiniz.

1. Bir C# proje şablonu projesi oluşturun (Visual Studio Yeni Dosya'Project  >    >   seçin ve "proje şablonu" araması yazın). **MyProjectTemplate olarak ad girin.**

   > [!NOTE]
   > Visual Studio SDK'yı yüklemeniz istenebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

2. Proje şablonu projesiyle aynı çözüme yeni bir VSIX projesi ekleyin **(Çözüm Gezgini'de** çözüm düğümünü seçin, sağ tıklayın ve Yeni  >  **Ekle'yi Project** ve "vsix" araması için arama). **MyProjectWizard olarak ad girin.**

3. VSIX projesini başlangıç projesi olarak ayarlayın. Bu **Çözüm Gezgini,** VSIX proje düğümünü seçin, sağ tıklayın ve Başlangıç Olarak **Ayarla'yı Project.**

4. Şablon projesini VSIX projesinin bir varlığı olarak ekleyin. Bu **Çözüm Gezgini,** VSIX proje düğümü altında *source.extension.vsixmanifest dosyasını* bulun. Bildirim düzenleyicisinde açmak için çift tıklayın.

5. Bildirim düzenleyicisinde pencerenin **sol** tarafındaki Varlıklar sekmesini seçin.

6. Varlıklar sekmesinde **Yeni'yi** **seçin.** Yeni Varlık **Ekle penceresindeki** Tür alanında **Microsoft.VisualStudio.ProjectTemplate öğesini seçin.** Kaynak **alanında Geçerli** çözümde **bir proje'yi seçin.** Yeni **Project** **MyProjectTemplate öğesini seçin.** Daha sonra, **Tamam**'a tıklayın.

7. Çözümü derleme ve hata ayıklamayı başlatma. İkinci bir örnek Visual Studio görüntülenir. (Bu birkaç dakika sürebilir.)

8. Visual Studio'nin ikinci örneğinde, yeni şablonunuzla ( Dosya YeniDosya  >    >  Project, "myproject" araması) yeni bir proje oluşturun. Yeni proje Class1 adlı bir **sınıfla görünse iyi olur.** Şimdi özel bir proje şablonu oluşturdun! Hata ayıklamayı hemen durdurun.

## <a name="create-a-custom-template-wizard"></a>Özel şablon oluşturma sihirbazı

Bu yordam, proje oluşturulmadan önce Bir Form Windows özel bir sihirbazın nasıl oluşturulacaklarını gösterir. Form, kullanıcıların proje oluşturma sırasında kaynak koda eklenen özel bir parametre değeri eklemesini sağlar.

1. VSIX projesini bir derleme oluşturmasına izin verecek şekilde ayarlayın.

2. Bu **Çözüm Gezgini** VSIX proje düğümünü seçin. Aşağıda **Çözüm Gezgini,** Özellikler penceresini **görüyor gerekir.** Bunu yapmadıysanız Özellikler Penceresini  >  **Görüntüle'yi seçin** veya **F4 tuşuna basın.** Özellikler **penceresinde,** için aşağıdaki alanları `true` seçin:

   - **VSIX kapsayıcısı içinde derlemeyi dahil edin**

   - **VSIX Kapsayıcısı'ne Hata Ayıklama Sembolleri Ekleme**

   - **Yerel VSIX Dağıtımına Hata Ayıklama Sembolleri Ekleme**

3. Derlemeyi VSIX projesine varlık olarak ekleyin. *source.extension.vsixmanifest dosyasını* açın ve **Varlıklar sekmesini** seçin. Yeni Varlık **Ekle penceresinde**  Tür olarak **Microsoft.VisualStudio.Assembly'i** seçin, Kaynak için  Geçerli çözümde bir proje'yi seçin ve Project **Için MyProjectWizard'ı seçin.**  

4. VSIX projesine aşağıdaki başvuruları ekleyin. (Çözüm Gezgini VSIX proje düğümünün altında Başvurular'ı **seçin,** sağ tıklayın ve Başvuru **Ekle'yi** seçin.) Başvuru **Ekle iletişim** kutusundaki Framework **sekmesinde** **System.Windows Forms derlemesini bulun** ve seçin. Ayrıca System ve  **System.Drawing derlemelerini bulup** seçin. Şimdi **Uzantılar sekmesini** seçin. **EnvDTE derlemesi** bulun ve seçin. **Ayrıca Microsoft.VisualStudio.TemplateWizardInterface derlemeyi** bulun ve seçin. **Tamam**'a tıklayın.

5. VSIX projesine sihirbaz uygulaması için bir sınıf ekleyin. (Çözüm Gezgini'de VSIX proje düğümüne sağ tıklayın ve **Ekle'yi,** ardından Yeni Öğe'yi ve **ardından** **Sınıf'ı** seçin.)  Sınıfa **WizardImplementation adını girin.**

6. *WizardImplementationClass.cs dosyasındaki kodu* aşağıdaki kodla değiştirin:

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

    Bu **kodda başvurulan UserInputForm** daha sonra uygulanacaktır.

    sınıfı, `WizardImplementation` her üyesi için yöntem uygulamaları <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> içerir. Bu örnekte, bir görevi <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> yalnızca yöntemi gerçekleştirir. Diğer tüm yöntemler hiçbir şey yapmaz veya dönüş `true` yapar.

    yöntemi <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> dört parametre kabul eder:

   - Projeyi <xref:System.Object> özelleştirmenize olanak sağlamak için <xref:EnvDTE._DTE> kök nesnesine değiştirebileceğiniz bir parametre.

   - Şablonda <xref:System.Collections.Generic.Dictionary%602> tüm önceden tanımlanmış parametrelerin koleksiyonunu içeren bir parametre. Şablon parametreleri hakkında daha fazla bilgi için [bkz. Şablon parametreleri.](../ide/template-parameters.md)

   - <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind>Kullanılan şablon türü hakkında bilgi içeren bir parametre.

   - Sihirbaz <xref:System.Object> tarafından sihirbaza geçirilen bir parametre kümesi içeren Visual Studio.

     Bu örnek, kullanıcı giriş formundan parametresine bir parametre değeri <xref:System.Collections.Generic.Dictionary%602> ekler. Projede `$custommessage$` parametrenin her örneği, kullanıcı tarafından girilen metinle değiştirilir.

7. Şimdi **UserInputForm oluşturun.** *WizardImplementation.cs* dosyasında, sınıfının sonundan sonra aşağıdaki kodu `WizardImplementation` ekleyin.

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

    Kullanıcı giriş formu, özel parametre girmek için basit bir form sağlar. Formda adlı bir metin kutusu `textBox1` ve adlı bir düğme `button1` vardır. Düğmeye tıklandığı zaman, metin kutusundan gelen metin parametresinde `customMessage` depolanır.

## <a name="connect-the-wizard-to-the-custom-template"></a>Bağlan özel şablona ekleme

Özel proje şablonunuz için özel sihirbazınızı kullanmak üzere, sihirbaz derlemesini imzalamanız ve yeni bir proje oluşturulduğunda sihirbaz uygulamasının nerede bulunacaklarını haber verecek şekilde özel proje şablonunuz için bazı satırlar eklemeniz gerekir.

1. Derlemeyi imzalar. Dosya **Çözüm Gezgini** VSIX projesini seçin, sağ tıklayın ve **Özellikler'i Project seçin.**

2. Project **penceresinde** İmzalama sekmesini **seçin.** İmzalama sekmesinde **Derlemeyi** **imzala'ya tıklayın.** Bir **güçlü ad anahtar dosyası seçin alanında** öğesini **\<New>** seçin. Güçlü **Ad Anahtarı Oluştur** penceresindeki Anahtar **dosyası adı alanına** **key.snk yazın.** Anahtar dosyamı **parolayla koru alanı işaretini** kaldırın.

3. Aşağıdaki **Çözüm Gezgini** VSIX projesini seçin ve Özellikler **penceresini** bulun.

4. Derleme **Çıktısını Çıkış Dizinine Kopyala alanını** true olarak **ayarlayın.** Bu, çözüm yeniden oluşturulurken derlemenin çıkış dizinine kopyalanır. Dosyada hala yer `.vsix` alan bir dosyadır. İmzalama anahtarını bulmak için derlemeyi görüyor gerekir.

5. Çözümü yeniden derleyin.

6. Artık key.snk dosyasını MyProjectWizard proje dizininde (*\<your disk location> \MyProjectTemplate\MyProjectWizard\key.snk*) bulabilirsiniz. *key.snk dosyasını* kopyalayın.

7. Çıkış dizinine gidin ve derlemeyi bulun (*\<your disk location> \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll*). *key.snk dosyasını buraya* yapıştırın. (Bu kesinlikle gerekli değildir, ancak aşağıdaki adımları kolaylaştırır.)

8. Bir komut penceresi açın ve derlemenin oluşturularak diziniyle değiştirebilirsiniz.

9. Yeni *sn.exe* aracını bulun. Örneğin, 64 bit Windows 10 bir işletim sisteminde tipik bir yol aşağıdaki gibi olabilir:

     *C:\Program Files (x86)\Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Araçları*

     Aracı bulamazsanız komut penceresinde **/R . sn.exe** çalıştırmayı deneyin. Yolu not alan bir not.

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
