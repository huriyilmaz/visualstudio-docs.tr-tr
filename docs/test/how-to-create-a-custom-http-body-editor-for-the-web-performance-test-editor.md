---
title: Web Performans Testi Düzenleyicisi için özel HTTP Gövde Düzenleyicisi oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 357114ad623494a26d98d3b190ed50847a0b27cd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664791"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Nasıl yapılır: Web Performans Testi Düzenleyicisi için özel HTTP Gövde Düzenleyicisi oluşturma

Dize gövdesi içeriğini veya bir Web hizmeti isteğinin ikili gövde içeriğini (örneğin, SOAP, REST, asmx, WCF, RıA ve diğer Web hizmeti istek türleri) düzenlemenizi sağlayan özel bir İçerik Düzenleyicisi oluşturabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bu tür düzenleyicilerin uygulanması için:

- **Dize İçerik Düzenleyicisi** Bu, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> arabirimi kullanılarak uygulanır.

- **İkili içerik Düzenleyicisi** Bu, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> arabirimi kullanılarak uygulanır.

Bu arabirimler <xref:Microsoft.VisualStudio.TestTools.WebTesting> ad alanında yer alır.

## <a name="create-a-windows-control-library-project"></a>Windows Denetim Kitaplığı projesi oluşturma

1. Visual Studio 'da yeni bir **Windows Forms denetim kitaplığı** projesi oluşturun. Proje **Messagedüzenleyicilerini**adlandırın.

   Proje yeni çözüme eklenir ve tasarımcıda *UserControl1.cs* adlı bir <xref:System.Windows.Forms.UserControl> sunulur.

1. **Araç kutusundan**, **ortak denetimler** kategorisi altında, UserControl1 yüzeyine bir <xref:System.Windows.Forms.RichTextBox> sürükleyin.

1. @No__t_2 denetiminin sağ üst köşesindeki eylem etiketi glifini (![Smart etiket karakter ](../test/media/vs_winformsmttagglyph.gif)) seçin ve ardından **üst kapsayıcıda**seçin ve yerleştirin.

1. **Çözüm Gezgini**, Windows Forms kitaplığı projesine sağ tıklayın ve **Özellikler**' i seçin.

1. **Özellikler**' de **uygulama** sekmesini seçin.

1. **Hedef çerçeve** açılan listesinde .NET Framework 4 (veya üzeri) öğesini seçin.

1. **Hedef çerçeve değişimi** iletişim kutusu görüntülenir.

1. **Evet**' i seçin.

1. **Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

1. **Başvuru Ekle** iletişim kutusu görüntülenir.

1. Öğesini seçin. **Net** Tab, aşağı kaydırın ve **Microsoft. VisualStudio. QualityTools. WebTestFramework** ' ı seçin ve ardından **Tamam**' ı seçin.

1. **Görünüm Tasarımcısı** hala açık değilse, **Çözüm Gezgini**' de, **UserControl1.cs** ' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' yi seçin.

1. Tasarım yüzeyinde sağ tıklayıp **kodu görüntüle**' yi seçin.

1. Seçim Sınıf adını ve oluşturucuyu, örnek olarak, MessageEditorControl gibi anlamlı bir adla değiştirin:

    > [!NOTE]
    > Örnek MessageEditorControl kullanır.

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

1. RichTextBox1 içinde metin almayı ve ayarlamayı etkinleştirmek için aşağıdaki özellikleri ekleyin. @No__t_0 arabirimi EditString kullanır ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> EditByteArray kullanır:

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

## <a name="add-a-class-to-the-windows-control-library-project"></a>Windows denetim kitaplığı projesine bir sınıf ekleme

Projeye bir sınıf ekleyin. @No__t_0 ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> arabirimlerini uygulamak için kullanılır.

**Bu yordamdaki koda genel bakış**

Önceki yordamda oluşturulan MessageEditorControl <xref:System.Windows.Forms.UserControl> messageEditorControl olarak oluşturulur:

```csharp
private MessageEditorControl messageEditorControl
```

MessageEditorControl örneği, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*> yöntemi tarafından oluşturulan eklenti iletişim kutusunda barındırılır. Ayrıca, messageEditorControl 'ın <xref:System.Windows.Forms.RichTextBox> <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> içeriğiyle doldurulur. Ancak, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> `true` döndürmediği takdirde eklentinin oluşturulması gerçekleştirilemez. Bu düzenleyici söz konusu olduğunda, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> "xml" içeriyorsa <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> `true` döndürür.

Dize gövdesinin düzenlenmesi tamamlandığında ve Kullanıcı eklenti iletişim kutusunda **Tamam** ' a tıkladığında, düzenlenmiş metni bir dize olarak almak ve Web test performansı Düzenleyicisi 'Ndeki Istekteki **dize gövdesini** güncelleştirmek için <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> çağırılır.

### <a name="create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface"></a>Bir sınıf oluşturun ve ıtringhttpbodyeditorplugin arabirimini uygulayın

1. **Çözüm Gezgini**' de, Windows Forms denetim kitaplığı projesine sağ tıklayın ve **Yeni öğe Ekle**' yi seçin.

   **Yeni öğe Ekle** iletişim kutusu görüntülenir.

2. **Sınıf**seçin.

3. **Ad** metin kutusuna sınıf için anlamlı bir ad yazın, örneğin `MessageEditorPlugins`.

4. **Ekle**' yi seçin.

   Class1 projeye eklenir ve kod düzenleyicisinde sunulur.

5. Kod Düzenleyicisi 'nde aşağıdaki `using` ifadesini ekleyin:

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

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Sınıfa bir IBinaryHttpBodyEditorPlugin ekleyin

@No__t_0 arabirimini uygulayın.

**Bu yordamdaki koda genel bakış**

@No__t_0 arabirimi için kod uygulama, önceki yordamda kapsanan <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> benzerdir. Ancak, ikili sürüm dize yerine ikili verileri işlemek için bir bayt dizisi kullanır.

İlk yordamda oluşturulan MessageEditorControl <xref:System.Windows.Forms.UserControl> messageEditorControl olarak oluşturulur:

```csharp
private MessageEditorControl messageEditorControl
```

MessageEditorControl örneği, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*> yöntemi tarafından oluşturulan eklenti iletişim kutusunda barındırılır. Ayrıca, messageEditorControl 'ın <xref:System.Windows.Forms.RichTextBox> <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> içeriğiyle doldurulur. Ancak, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> `true` döndürmediği takdirde eklentinin oluşturulması gerçekleştirilemez. Bu düzenleyici söz konusu olduğunda, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> "msbin1" içeriyorsa <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> `true` döndürür.

Dize gövdesinin düzenlenmesi tamamlandığında ve Kullanıcı eklenti iletişim kutusunda **Tamam** ' a tıkladığında, düzenlenmiş metni bir dize olarak almak ve Web test performansı Düzenleyicisi 'Ndeki Istekteki **BinaryHttpBody. Data** öğesini güncelleştirmek için <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> çağırılır.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>Sınıfına IBinaryHttpBodyEditorPlugin eklemek için

- @No__t_0 arabiriminden Msbin1MessageEditor sınıfının örneğini oluşturmak ve gerekli yöntemleri uygulamak için önceki yordamda eklenen XmlMessageEditor sınıfının altına aşağıdaki kodu yazın veya kopyalayın:

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

## <a name="build-and-deploy-the-plug-ins"></a>Eklentileri derleme ve dağıtma

1. **Yapı** menüsünde, **Yapı \<Windows Form denetim kitaplığı proje adı >** ' nı seçin.

2. Visual Studio 'nun tüm örneklerini kapatın.

   > [!NOTE]
   > Visual Studio 'Yu kapatmak, kopyalamayı denemeden önce *. dll* dosyasının kilitlenmediğinden emin olmanızı sağlar.

3. Elde edilen *. dll* dosyasını projenizin *bin\Debug* klasöründen (örneğin, *messagedüzenleyiciler. dll*) *%programfiles%\microsoft Visual studio\2017 \\ \<edition > \Common7\IDE\PrivateAssemblies\ 'e kopyalayın. WebTestPlugins*.

4. Visual Studio'yu açın.

   *. Dll* artık Visual Studio ile kaydedilir.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Web performans testini kullanarak eklentileri doğrulama

1. Bir test projesi oluşturun.

2. Web performans testi oluşturun ve bir Web hizmetine tarayıcıda bir URL girin.

3. Kaydı tamamladığınızda, Web Performans Testi Düzenleyicisi Web hizmeti için isteği genişletin ve bir **dize gövdesi** ya da **ikili gövde**seçin.

4. **Özellikler** penceresinde, dize gövdesi veya ikili gövde ' yi seçin ve üç nokta **(...)** simgesini seçin.

   **Http gövde verilerini Düzenle** iletişim kutusu görüntülenir.

5. Artık verileri düzenleyebilir ve **Tamam**' ı seçebilirsiniz. Bu, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> içeriğini güncelleştirmek için geçerli GetNewValue yöntemini çağırır.

## <a name="compile-the-code"></a>Kodu derle

Windows Denetim Kitaplığı projesi için hedeflenen Framework 'ün .NET Framework 4,5 olduğunu doğrulayın. Varsayılan olarak, Windows denetim kitaplığı projeleri, Microsoft. VisualStudio. QualityTools. WebTestFramework başvurusunun eklenmesine izin vermeyecek .NET Framework 4,5 Istemci çerçevesini hedefleyin.

Daha fazla bilgi için bkz. [uygulama sayfası, proje TasarımcısıC#()](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl yapılır: istek düzeyi eklentisi oluşturma](../test/how-to-create-a-request-level-plug-in.md)
- [Web performans testi için özel bir ayıklama kuralı kodlayın](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Web performans testi için özel doğrulama kuralı kodu oluşturma](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Nasıl yapılır: yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)
- [Kodlanmış Web performans testi oluşturma ve çalıştırma](../test/generate-and-run-a-coded-web-performance-test.md)
- [Nasıl yapılır: Web performans Test Sonuçları Görüntüleyicisi için Visual Studio eklentisi oluşturma](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)