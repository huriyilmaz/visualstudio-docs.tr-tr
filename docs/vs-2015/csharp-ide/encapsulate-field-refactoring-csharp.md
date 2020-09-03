---
title: Alanı yeniden düzenlemeyi yalıtma (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b4f5ddbe7eab925b06584f00b04bed3c74e9811
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667567"
---
# <a name="encapsulate-field-refactoring-c"></a>Alan Yeniden Düzenlemesini Yalıtma (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Alanı yalıtma** yeniden düzenleme işlemi, var olan bir alandan hızlıca bir özellik oluşturmanıza ve ardından kodunuzu yeni özelliğe başvurularla sorunsuzca güncelleştirmenize olanak sağlar.

 Bir [alan](https://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) [genel](https://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e)olduğunda, diğer nesnelerin bu alana doğrudan erişimi vardır ve bu alana sahip olan nesne tarafından algılanarak değişiklik yapabilir. Bu alanı kapsüllemek için [özellikleri](https://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) kullanarak alanlara doğrudan erişime izin vermemeyi sağlayabilirsiniz.

 Yeni özelliği oluşturmak için, **alanı yalıtma** işlemi, [özel](https://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8)olarak kapsüllemek istediğiniz alanın erişim değiştiricisini değiştirir ve ardından bu alan için [Get](https://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71) ve [set](https://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) erişimcileri oluşturur. Bazı durumlarda, yalnızca bir `get` erişimci oluşturulur (örneğin, alanın salt okunurdur olarak bildirildiği gibi).

 Yeniden düzenleme motoru, kodunuzu, **alanı yalıtma** Iletişim kutusunun **başvuruları güncelleştir** bölümünde belirtilen alanlardaki yeni özelliğe başvurularla güncelleştirir.

### <a name="to-create-a-property-from-a-field"></a>Bir alandan özellik oluşturmak için

1. Adlı bir konsol uygulaması oluşturun `EncapsulateFieldExample` ve ardından `Program` Aşağıdaki örnek kodla değiştirin.

    ```csharp
    class Square
    {
        // Select the word 'width' and then use Encapsulate Field.
        public int width, height;
    }
    class MainClass
    {
        public static void Main()
        {
            Square mySquare = new Square();
            mySquare.width = 110;
            mySquare.height = 150;
            // Output values for width and height.
            Console.WriteLine("width = {0}", mySquare.width);
            Console.WriteLine("height = {0}", mySquare.height);
        }
    }
    ```

2. [Kod Düzenleyicisi](../ide/writing-code-in-the-code-and-text-editor.md)'nde, imleci, kapsüllemek istediğiniz alanın adına, bildirime yerleştirin. Aşağıdaki örnekte, imleci sözcüğe yerleştirin `width` :

    ```csharp
    public int width, height;
    ```

3. Yeniden **Düzenle** menüsünde **alanı kapsülle**' ye tıklayın.

     **Alanı yalıtma** iletişim kutusu görüntülenir.

     Ayrıca, **alanı kapsülle** iletişim kutusunu göstermek için CTRL + R, E klavye kısayolunu da yazabilirsiniz.

     Ayrıca imleci sağ tıklayıp yeniden **Düzenle**' nin üzerine **gelip alanı** kapsülle ' ya tıklayarak **alanı kapsülle** iletişim kutusunu görüntüleyebilirsiniz.

4. Ayarları belirtin.

5. ENTER tuşuna basın veya **Tamam** düğmesine tıklayın.

6. **Başvuru değişikliklerini Önizle** seçeneğini belirlediyseniz, **başvuru değişikliklerini Önizle** penceresi açılır. **Uygula** düğmesine tıklayın.

     `get` `set` Kaynak dosyanızda aşağıdaki ve erişimci kodu görüntülenir:

    ```csharp
    public int Width
    {
        get { return width; }
        set { width = value; }
    }
    ```

     Yöntemdeki kod, `Main` Yeni `Width` özellik adına de güncelleştirilir.

    ```csharp
    Square mySquare = new Square();
    mySquare.Width = 110;
    mySquare.height = 150;
    // Output values for width and height.
    Console.WriteLine("width = {0}", mySquare.Width);
    ```

## <a name="remarks"></a>Açıklamalar
 **Alanı yalıtma** işlemi, yalnızca imleç alan bildirimiyle aynı satıra yerleştirildiğinde mümkündür.

 Birden çok alanı bildiren bildirimler için **alanı yalıtma** alanları arasında bir sınır olarak virgül kullanır ve imlecin en yakın alanında ve imleç ile aynı satırda yeniden düzenleme başlatılır. Ayrıca, bildirimdeki ilgili alanın adını seçerek hangi alanı kapsüllemek istediğinizi de belirtebilirsiniz.

 Bu yeniden düzenleme işlemi tarafından oluşturulan kod, alan kodu parçacıklarını yalıtma özelliğiyle modellenir. Kod parçacıkları değiştirilebilir. Daha fazla bilgi için bkz. [kod parçacıkları](../ide/code-snippets.md).

## <a name="see-also"></a>Ayrıca Bkz.
 Yeniden [düzenleme (C#)](../csharp-ide/refactoring-csharp.md) [Visual C# kod parçacıkları](../ide/visual-csharp-code-snippets.md)