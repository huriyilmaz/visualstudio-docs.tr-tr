---
title: Web Performans Testi Düzenleyicisi için özel HTTP gövde düzenleyicisi oluşturun
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efc9a959fa02b62583e7bf366e8c580b2876a4a1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589207"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Nasıl?

Soap, REST, asmx, wcf, RIA ve diğer web hizmeti isteği türleri gibi, dize gövdesi içeriğini veya bir web hizmeti isteğinin ikili gövde içeriğini oluşturmanızı sağlayan özel bir içerik düzenleyicisi oluşturabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bu tür editörleri uygulayabilirsiniz:

- **String içerik düzenleyicisi** Bu <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> arabirim kullanılarak uygulanır.

- **İkili içerik düzenleyicisi** Bu <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> arabirim kullanılarak uygulanır.

Bu arabirimler <xref:Microsoft.VisualStudio.TestTools.WebTesting> ad alanında bulunur.

## <a name="create-a-windows-control-library-project"></a>Windows Denetim Kitaplığı projesi oluşturma

1. Visual Studio'da yeni bir **Windows Forms Control Library** projesi oluşturun. **ProjeMessageEditors**adı .

   Proje yeni çözüme eklenir ve <xref:System.Windows.Forms.UserControl> *tasarımcıda* UserControl1.cs adlı bir şekilde sunulur.

1. Ortak **Denetimler** kategorisi altında araç <xref:System.Windows.Forms.RichTextBox> **kutusundan,** Bir'i UserControl1'in yüzeyine sürükleyin.

1. Denetimin sağ üst köşesindeki eylem![etiketi glyph 'i (Smart Tag](../test/media/vs_winformsmttagglyph.gif)Glyph) seçin ve ardından Üst **Kapsayıcı'da**seçip Sabitleyin. <xref:System.Windows.Forms.RichTextBox>

1. **Çözüm Gezgini'nde,** Windows Forms Library projesine sağ tıklayın ve **Özellikler'i**seçin.

1. **Özellikler'de,** **Uygulama** sekmesini seçin.

1. Hedef **çerçeve** açılır listesinde .NET Framework 4 (veya sonraki) seçeneğini belirleyin.

1. **Hedef Çerçeve Değişikliği** iletişim kutusu görüntülenir.

1. **Evet'i**seçin.

1. **Çözüm Gezgini'nde,** **Başvurular** düğümüne sağ tıklayın ve **Referans Ekle'yi**seçin.

1. **Başvuru Ekle** iletişim kutusu görüntülenir.

1. Seçin . **NET** sekmesi, aşağı kaydırın ve **Microsoft.VisualStudio.QualityTools.WebTestFramework** seçin ve sonra **Tamam**seçin.

1. **Görünüm Tasarımcısı** hala açık değilse, **Çözüm Gezgini'nde** **UserControl1.cs** sağ tıklatın ve ardından **Tasarımcıyı Görüntüle'yi**seçin.

1. Tasarım yüzeyinde, Sağ tıklayın ve **Kodu Görüntüle'yi**seçin.

1. (İsteğe bağlı) Sınıfın ve oluşturucunun adını UserControl1'den anlamlı bir ada (örneğin, MessageEditorControl: MessageEditorControl) değiştirin:

    > [!NOTE]
    > Örnek, MessageEditorControl'u kullanır.

    ```csharp
    namespace MessageEditors
    {
        public partial class MessageEditorControl : UserControl
        {
            public MessageEditorControl()
            {
                InitializeComponent();
            }
        }
    }
    ```

1. RichTextBox1'de metnin alınıp ayarlanmasını etkinleştirmek için aşağıdaki özellikleri ekleyin. Arayüz <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> EditString <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> ve EditByteArray kullanır:

    ```csharp
    public String EditString
    {
       get
       {
           return this.richTextBox1.Text;
       }
       set
       {
           this.richTextBox1.Text = value;
       }
    }

    public byte[] EditByteArray
    {
       get
       {
           return System.Convert.FromBase64String(richTextBox1.Text);
       }
       set
       {
           richTextBox1.Text = System.Convert.ToBase64String(value, 0, value.Length);
       }
    }
    ```

## <a name="add-a-class-to-the-windows-control-library-project"></a>Windows Denetim Kitaplığı projesine sınıf ekleme

Projeye bir sınıf ekleyin. Bu <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> arayüzleri uygulamak için kullanılacaktır.

**Bu yordamdaki koda genel bakış**

Önceki yordamda <xref:System.Windows.Forms.UserControl> oluşturulan MessageEditorControl iletiDüzenleyici Denetim olarak anında verilir:

```csharp
private MessageEditorControl messageEditorControl
```

MessageEditorControl <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*> örneği, yöntem tarafından oluşturulan eklenti iletişim kutusunda barındırılır. Ayrıca, iletiEditorControl's <xref:System.Windows.Forms.RichTextBox> içindekilerle <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>doldurulur. Ancak, döndürülmedikçe <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> `true`eklentinin oluşturulması gerçekleşemez. Bu editör <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> durumunda, içinde `true` "xml" <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> varsa döndürür.

Dize gövdesinin düzenlenmesi tamamlandığında ve kullanıcı eklenti iletişim kutusunda **Tamam'ı** tıklattığında, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> düzenlenen metni dize olarak almak ve Web Test Performans Düzenleyicisi'ndeki istekte **String Gövdesini** güncelleştirmek için çağrılır.

### <a name="create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface"></a>Bir sınıf oluşturun ve IStringHttpBodyEditorPlugin arabirimini uygulayın

1. **Çözüm Gezgini'nde,** Windows Forms Control Library projesine sağ tıklayın ve Yeni **Öğe Ekle'yi**seçin.

   **Yeni Öğe Ekle** iletişim kutusu görüntülenir.

2. **Sınıf'ı**seçin.

3. **Ad** metin kutusuna, sınıf için anlamlı bir ad `MessageEditorPlugins`yazın, örneğin.

4. **Ekle'yi**seçin.

   Sınıf1 projeye eklenir ve Kod Düzenleyicisi'nde sunulur.

5. Kod düzenleyicisinde aşağıdaki `using` ifadeyi ekleyin:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

6. Arabirimi uygulamak için aşağıdaki kodu yapıştırın:

    ```csharp
    /// <summary>
    /// Editor for generic text based hierarchical messages such as XML and JSON.
    /// </summary>
    public class XmlMessageEditor : IStringHttpBodyEditorPlugin
    {
        public XmlMessageEditor()
        {
        }

        /// <summary>
        /// Determine if this plugin supports the content type.
        /// </summary>
        /// <param name="contentType">The content type to test.</param>
        /// <returns>Returns true if the plugin supports the specified content type.</returns>
        public bool SupportsContentType(string contentType)
        {
            return contentType.ToLower().Contains("xml");
        }

        /// <summary>
        /// Create a UserControl to edit the specified bytes.
        /// This control will be hosted in the
        /// plugin dialog which provides OK and Cancel buttons.
        /// </summary>
        /// <param name="contentType">The content type of the BinaryHttpBody.</param>
        /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
        /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
        public object CreateEditor(string contentType, string initialValue)
        {
            messageEditorControl = new MessageEditorControl();
            messageEditorControl.EditString = initialValue;
            return this.messageEditorControl;
        }

        /// <summary>
        /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
        /// </summary>
        public string GetNewValue()
        {
            return messageEditorControl.EditString;
        }

        private MessageEditorControl messageEditorControl;
    }
    ```

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Sınıfa Bir IBinaryHttpBodyEditorPlugin ekleyin

<xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> arabirimini gerçekleştirin.

**Bu yordamdaki koda genel bakış**

<xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> Arabirim in kod uygulaması önceki <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> yordamda kapsanana benzer. Ancak, ikili sürüm, bir dize yerine ikili verileri işlemek için bir dizi bayt kullanır.

İlk yordamda <xref:System.Windows.Forms.UserControl> oluşturulan MessageEditorControl, messageEditorControl olarak anında verilir:

```csharp
private MessageEditorControl messageEditorControl
```

MessageEditorControl <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*> örneği, yöntem tarafından oluşturulan eklenti iletişim kutusunda barındırılır. Ayrıca, iletiEditorControl's <xref:System.Windows.Forms.RichTextBox> içindekilerle <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>doldurulur. Ancak, döndürülmedikçe <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> `true`eklentinin oluşturulması gerçekleşemez. Bu editör <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> durumunda, içinde `true` "msbin1" <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> varsa döndürür.

Dize gövdesinin düzenlenmesi tamamlandığında ve kullanıcı eklenti iletişim kutusunda **Tamam'ı** tıklattığında, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> düzenlenen metni dize olarak almak ve Web Test Performans Düzenleyicisi'ndeki istekte **BinaryHttpBody.Data'yı** güncelleştirmek için çağrılır.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>IBinaryHttpBodyEditorPlugin'i sınıfa eklemek için

- Msbin1MessageEditor sınıfını arabirimden <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> anında çıkarmak ve gerekli yöntemleri uygulamak için önceki yordamda eklenen XmlMessageEditor sınıfının altında aşağıdaki kodu yazın veya kopyalayın:

    ```csharp
    /// <summary>
        /// Editor for MSBin1 content type (WCF messages)
        /// </summary>
        public class Msbin1MessageEditor : IBinaryHttpBodyEditorPlugin
        {
            /// <summary>
            ///
            /// </summary>
            public Msbin1MessageEditor()
            {
            }

            /// <summary>
            /// Determine if this plugin supports a content type.
            /// </summary>
            /// <param name="contentType">The content type to test.</param>
            /// <returns>Returns true if the plugin supports the specified content type.</returns>
            public bool SupportsContentType(string contentType)
            {
                return contentType.ToLower().Contains("msbin1");
            }

            /// <summary>
            /// Create a UserControl to edit the specified bytes. This control will be hosted in the
            /// plugin dialog which provides OK and Cancel buttons.
            /// </summary>
            /// <param name="contentType">The content type of the BinaryHttpBody.</param>
            /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
            /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
            public object CreateEditor(string contentType, byte[] initialValue)
            {
                messageEditorControl = new MessageEditorControl();
                messageEditorControl.EditByteArray = initialValue;
                return messageEditorControl;
            }

            /// <summary>
            /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
            /// </summary>
            public byte[] GetNewValue()
            {
                return messageEditorControl.EditByteArray;
            }

            private MessageEditorControl messageEditorControl;
            private object originalMessage;
        }
    ```

## <a name="build-and-deploy-the-plug-ins"></a>Eklentileri oluşturma ve dağıtma

1. **Yapı** menüsünde, **Yapı \<Windows Form Denetim Kitaplığı proje adı>'yi **seçin.

2. Visual Studio'nun tüm örneklerini kapatın.

   > [!NOTE]
   > Visual Studio'yu kapatmak, kopyalamaya çalışmadan önce *.dll* dosyasının kilitli olmadığından emin olur.

3. Sonuç *.dll* dosyasını projenizin *bin\debug* klasöründen (örneğin, *MessageEditors.dll)* *%ProgramFiles%\Microsoft Visual\\\<Studio\2017 sürümüne kopyalayın>\Common7\IDE\PrivateAssemblies\WebTestPlugins*.

4. Visual Studio'yu açın.

   *.dll* artık Visual Studio'ya kayıtlı.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Web Performans Testi kullanarak eklentileri doğrulama

1. Bir test projesi oluşturun.

2. Bir web performans testi oluşturun ve tarayıcıya bir URL girin.

3. Web Performans Testi Düzenleyicisi'nde kaydı tamamladığınızda, web hizmeti isteğini genişletin ve String **Gövdesi** veya **İkili Gövde'yi**seçin.

4. **Özellikler** penceresinde, String Body veya İkili Gövde'yi seçin ve elipsleri **seçin (...)**.

   HTTP Body Data iletişim kutusunu **edit** görüntülenir.

5. Artık verileri ve **Tamam'ı**seçebilirsiniz. Bu, içindekileri güncelleştirmek için geçerli GetNewValue yöntemini <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>çağırır.

## <a name="compile-the-code"></a>Kodu derleme

Windows Denetim Kitaplığı projesi için hedeflenen çerçevenin .NET Framework 4.5 olduğunu doğrulayın. Varsayılan olarak, Windows Denetim Kitaplığı projeleri Microsoft.VisualStudio.QualityTools.WebTestFramework başvurusu eklenmesine izin vermez .NET Framework 4.5 Istemci çerçevesini hedefleyin.

Daha fazla bilgi için [Uygulama sayfasına, proje tasarımcısına (C#)](../ide/reference/application-page-project-designer-csharp.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl yapilir: İstek düzeyi eklentisi oluşturma](../test/how-to-create-a-request-level-plug-in.md)
- [Web performans testi için özel bir çıkarma kuralı kodlama](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Web performans testi için özel doğrulama kuralını kodlama](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Nasıl yapılsın: Yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)
- [Kodlanmış web performans testi oluşturma](../test/generate-and-run-a-coded-web-performance-test.md)
- [Nasıl yapIlir: Web Performans Testi Sonuçları Görüntüleyicisi için Visual Studio eklentisi oluşturma](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)
