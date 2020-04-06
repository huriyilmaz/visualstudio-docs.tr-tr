---
title: 'Nasıl Yapılır: Sihirbazları Proje Şablonlarıyla Kullanma'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d2dc057dfa518bb52c6ba4d30cd0f3e0a822cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710541"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Nasıl kullanılır: Proje şablonları ile sihirbazları kullanma

Visual Studio, <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> uygulandığında, bir kullanıcı bir şablondan proje oluşturduğunda özel kod çalıştırmanızı sağlayan arabirimi sağlar.

Proje şablonu özelleştirme, şablonu özelleştirmek, şablona ek dosyalar eklemek veya projede izin verilen başka bir eylem için kullanıcı girişi toplayan özel kullanıcı arabirimi görüntülemek için kullanılabilir.

Arabirim <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> yöntemleri, bir kullanıcı **Yeni Proje** iletişim kutusunda **Tamam'ı** tıklattığı andan itibaren, proje oluşturulurken çeşitli zamanlarda çağrılır. Arabirimin her yöntemi, çağrıldığı noktayı açıklamak için adlandırılır. Örneğin, Visual Studio <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> projeyi oluşturmaya başladığında hemen arar ve kullanıcı girişi toplamak için özel kod yazmak için iyi bir konum oluşturur.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>VSIX projesiyle proje şablonu projesi oluşturma

Visual Studio SDK'nın bir parçası olan proje şablonu projesiyle özel bir şablon oluşturmaya başlarsınız. Bu yordamda, bir C# proje şablonu projesi kullanacağız, ancak Visual Basic proje şablonu projesi de vardır. Ardından, proje şablonu projesini içeren çözüme bir VSIX projesi eklersiniz.

1. C# proje şablonu projesi oluşturun (Visual Studio'da **Dosya** > **Yeni** > **Projesi'ni** seçin ve "proje şablonu" için arama yapın). Adını **MyProjectTemplate**.

   > [!NOTE]
   > Visual Studio SDK'yı yüklemeniz istenebilir. Daha fazla bilgi için Visual [Studio SDK'yı yükleme ye](../extensibility/installing-the-visual-studio-sdk.md)bakın.

2. Proje şablonu projesiyle aynı çözüme yeni bir VSIX projesi ekleyin **(Çözüm Gezgini'nde**çözüm düğümünü seçin, sağ tıklayın ve**Yeni Proje** **Ekle'yi** > seçin ve "vsix" için arama yapın). Adını **MyProjectWizard.**

3. VSIX projesini başlangıç projesi olarak ayarlayın. **Çözüm Gezgini'nde**VSIX proje düğümünü, sağ tıklatma yı ve **Başlangıç Projesi olarak Ayarla'yı**seçin.

4. Şablon projesini VSIX projesinin bir varlığı olarak ekleyin. **Solution**Explorer'da, VSIX proje düğümü altında *source.extension.vsixmanifest* dosyasını bulun. Manifesto düzenleyicisinde açmak için çift tıklatın.

5. Bildirim düzenleyicisinde, pencerenin sol tarafındaki **Varlıklar** sekmesini seçin.

6. **Varlıklar** sekmesinde **Yeni'yi**seçin. Yeni **Varlık Ekle** penceresinde, Tür alanı için **Microsoft.VisualStudio.ProjectTemplate'i**seçin. **Kaynak** alanında, **geçerli çözümde A projesi'ni**seçin. **Proje** alanında **MyProjectTemplate'i**seçin. Ardından **Tamam**'a tıklayın.

7. Çözümü oluşturun ve hata ayıklamaya başlayın. Visual Studio'nun ikinci bir örneği görüntülenir. (Bu işlem birkaç dakika sürebilir.)

8. Visual Studio'nun ikinci örneğinde, yeni şablonunla yeni bir proje oluşturmaya çalışın **(Dosya** > **Yeni** > **Projesi**, "myproject" arama). Yeni proje **Class1**adlı bir sınıf ile görünmelidir. Şimdi özel bir proje şablonu oluşturduk! Hata ayıklamayı hemen kes.

## <a name="create-a-custom-template-wizard"></a>Özel şablon sihirbazı oluşturma

Bu yordam, proje oluşturulmadan önce bir Windows Formu'nu açan özel bir sihirbazın nasıl oluşturulutur gösteriş gösterir. Form, kullanıcıların proje oluşturma sırasında kaynak koduna eklenen özel bir parametre değeri eklemesine olanak tanır.

1. Bir derleme oluşturmasına izin verecek Şekilde VSIX projesini ayarlayın.

2. **Çözüm Gezgini'nde**VSIX proje düğümünü seçin. **Çözüm Gezgini'nin**altında **Özellikler** penceresini görmeniz gerekir. Yoksa, Özellikleri **Görüntüle** > **Pencere'yi**seçin veya **F4**tuşuna basın. **Özellikler** penceresinde aşağıdaki alanları `true`seçin:

   - **VSIX Konteynerinde Montaj Dahil Et**

   - **Hata Ayıklama Sembollerini VSIX Konteynerine Dahil Et**

   - **Yerel VSIX Dağıtımına Hata Ayıklama Sembolleri Ekleme**

3. Derlemeyi VSIX projesine kıymet olarak ekleyin. *source.extension.vsixmanifest* dosyasını açın ve **Varlıklar** sekmesini seçin. Yeni **Varlık Ekle** penceresinde, **Microsoft.VisualStudio.Assembly** **yazın,** **Kaynak** için **geçerli çözümde bir proje**seçin ve **Project** için **MyProjectWizard'ı**seçin.

4. VSIX projesine aşağıdaki başvuruları ekleyin. (Solution **Solution Explorer**Explorer'da, VSIX proje düğümü **altında, Başvurular'ı**seçin , sağ tıklatın ve Başvuru **Ekle'yi**seçin .) Başvuru **Ekle** iletişim kutusunda, **Framework** sekmesinde **System.Windows Forms** derlemesini bulun ve seçin. Ayrıca **Sistem** ve **System.Drawing** montajlarını bulun ve seçin. Şimdi **Uzantılar** sekmesini seçin. **EnvDTE** derlemesini bulun ve seçin. Ayrıca **Microsoft.VisualStudio.TemplateWizardInterface** derlemesini bulun ve seçin. **Tamam**'a tıklayın.

5. VSIX projesine sihirbaz uygulaması için bir sınıf ekleyin. (Çözüm **Gezgini'nde,** VSIX proje düğümüne sağ tıklayın ve **Ekle'yi**seçin, sonra **Yeni Öğe**, sonra **Sınıf**.) Sınıf **Sihirbazı Uygulama**adı .

6. *WizardImplementationClass.cs* dosyasındaki kodu aşağıdaki kodla değiştirin:

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

    Bu kodda başvurulan **UserInputForm** daha sonra uygulanacaktır.

    Sınıf, `WizardImplementation` <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>her üye için yöntem uygulamaları içerir. Bu örnekte, <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> yalnızca yöntem bir görev gerçekleştirir. Diğer tüm yöntemler ya `true`hiçbir şey yapmak ya da dönmek.

    Yöntem <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> dört parametre kabul eder:

   - Projeyi özelleştirmenizi sağlamak için <xref:System.Object> <xref:EnvDTE._DTE> kök nesneye atılabilen bir parametre.

   - Şablondaki önceden tanımlanmış tüm parametrelerin bir koleksiyonunu içeren bir <xref:System.Collections.Generic.Dictionary%602> parametre. Şablon parametreleri hakkında daha fazla bilgi için [Şablon parametrelerine](../ide/template-parameters.md)bakın.

   - Ne <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> tür şablonlar kullanıldığına ilişkin bilgi içeren bir parametre.

   - <xref:System.Object> Visual Studio tarafından sihirbaza geçirilen bir dizi parametre içerir.

     Bu örnek, kullanıcı giriş formundan <xref:System.Collections.Generic.Dictionary%602> parametreye bir parametre değeri ekler. Projedeki parametrenin `$custommessage$` her örneği kullanıcı tarafından girilen metinle değiştirilir.

7. Şimdi **UserInputForm**oluşturun. *WizardImplementation.cs* dosyasında, `WizardImplementation` sınıfın sonundan sonra aşağıdaki kodu ekleyin.

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

    Kullanıcı giriş formu özel bir parametre girmek için basit bir form sağlar. Form, adlı `textBox1` bir metin kutusu `button1`ve . Düğme tıklatıldığında, metin kutusundaki metin `customMessage` parametrede depolanır.

## <a name="connect-the-wizard-to-the-custom-template"></a>Sihirbazı özel şablona bağlayın

Özel proje şablonunuzun özel sihirbazınızı kullanabilmesi için sihirbaz derlemesini imzalamanız ve yeni bir proje oluşturulduğunda sihirbaz uygulamasını nerede bulacağını bildirmek için özel proje şablonunuza bazı satırlar eklemeniz gerekir.

1. Montajı imzalayın. Çözüm **Gezgini'nde**VSIX projesini seçin, sağ tıklatın ve **Project Properties'i**seçin.

2. Project **Properties** penceresinde, **Sign the assembly** **İmzasekmesi'ni** seçin. **Signing** Güçlü **bir ad anahtarı dosya** alanı seç'te ** \<Yeni>'yi **seçin. Güçlü **Ad Anahtarı Oluştur** penceresinde, **Anahtar dosya adı** alanında **key.snk**yazın. **Anahtar dosyamı parola alanıyla koruyun'un** işaretlerini kaldırın.

3. Çözüm **Gezgini'nde**VSIX projesini seçin ve **Özellikler** penceresini bulun.

4. Kopya **Oluşturma Çıktısını Çıktı Dizini** alanına **doğru**olarak ayarlayın. Bu, çözüm yeniden oluşturulunca derlemenin çıktı dizinine kopyalanmasını sağlar. Hala `.vsix` dosyada yer almaktadır. İmza anahtarını bulmak için derlemeyi görmeniz gerekir.

5. Çözümü yeniden derleyin.

6. Şimdi Key.snk dosyasını MyProjectWizard proje dizininde*\<(disk konumunuz>\MyProjectTemplate\MyProjectWizard\key.snk)* bulabilirsiniz. *Key.snk* dosyasını kopyalayın.

7. Çıktı dizinine gidin ve derlemeyi bulun*\<(disk konumunuz>\MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll).* *Key.snk* dosyasını buraya yapıştırın. (Bu kesinlikle gerekli değildir, ancak aşağıdaki adımları kolaylaştırır.)

8. Komut penceresini açın ve derlemenin oluşturulduğu dizine değiştirin.

9. *sn.exe* imzalama aracını bulun. Örneğin, Bir Windows 10 64-bit işletim sisteminde, tipik bir yol aşağıdaki gibi olacaktır:

     *C:\Program Dosyaları (x86)\Microsoft SDK'lar\Windows\v10.0A\bin\NETFX 4.6.1 Araçlar*

     Aracı bulamıyorsanız, komut penceresinde **/R . sn.exe'nin bulunduğu yerde** çalıştırmayı deneyin. Yolu not edin.

10. *Anahtar.snk* dosyasından ortak anahtarı ayıklayın. Komut penceresinde,

     **\<sn.exe>\sn.exe -p key.snk outfile.key konumu.**

     Dizin adlarında boşluklar varsa *sn.exe'nin* yolunu tırnak işaretleriyle çevrelemeyi unutmayın!

11. Dış dosyadan ortak anahtar belirteci alın:

     **\<sn.exe>\sn.exe -t outfile.key konumu.**

     Yine, tırnak işaretlerini unutmayın. Çıktıda böyle bir çizgi görmelisiniz.

     **Genel anahtar belirteci>belirteçtir \<**

     Bu değere dikkat edin.

12. Proje şablonunun *.vstemplate* dosyasına özel sihirbaza başvuru ekleyin. Çözüm **Gezgini'nde** *MyProjectTemplate.vstemplate*adlı dosyayı bulun ve açın. \<TemplateContent> bölümünün sonunda aşağıdaki bölümü ekleyin:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     **MyProjectWizard** derlemenin adı dır ve **belirteç** önceki adımda kopyaladığınız belirteçtir.

13. Projedeki tüm dosyaları kaydedin ve yeniden yeniden oluşturun.

## <a name="add-the-custom-parameter-to-the-template"></a>Şablona özel parametre ekleme

Bu örnekte, şablon olarak kullanılan proje, özel sihirbazın kullanıcı giriş formunda belirtilen iletiyi görüntüler.

1. Çözüm **Gezgini'nde** **MyProjectTemplate** projesine gidin ve *Class1.cs*açın.

2. Uygulama `Main` yönteminde aşağıdaki kod satırını ekleyin.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Parametre, `$custommessage$` şablondan bir proje oluşturulduğunda kullanıcı giriş formuna girilen metinle değiştirilir.

Burada bir şablona dışa aktarılmadan önce tam kod dosyası.

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

## <a name="use-the-custom-wizard"></a>Özel sihirbazı kullanma

Artık şablonunuzdan bir proje oluşturabilir ve özel sihirbazı kullanabilirsiniz.

1. Çözümü yeniden oluştur ve hata ayıklamaya başlayın. Visual Studio'nun ikinci bir örneği görünmelidir.

2. Yeni bir MyProjectTemplate projesi oluşturun. (**Dosya** > **Yeni** > **Proje**).

3. Yeni **Proje** iletişim kutusunda, şablonunuzu bulmak için "myproject"i arayın, bir ad yazın ve **Tamam'ı**tıklatın.

     Sihirbaz kullanıcı giriş formu açılır.

4. Özel parametre için bir değer yazın ve düğmeyi tıklatın.

     Sihirbaz kullanıcı girişi formu kapanır ve şablondan bir proje oluşturulur.

5. **Çözüm Gezgini'nde**kaynak kod dosyasına sağ tıklayın ve **Kodu Görüntüle'yi**tıklatın.

     `$custommessage$` Sihirbaz kullanıcı giriş formunda girilen metinle değiştirilene dikkat edin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Sihirbazuzatma öğesi (Visual Studio şablonları)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Visual Studio şablonlarında NuGet paketleri](/nuget/visual-studio-extensibility/visual-studio-templates)
