---
title: L2DBForm.xaml.cs kaynak kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 5a40dad3-6763-4576-b3ad-874df3f2c8d9
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3f783161865092f714955b65e6f2fa4791741cbe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664283"
---
# <a name="l2dbformxamlcs-source-code"></a>L2DBForm.xaml.cs Kaynak Kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, L2DBForm.xaml.cs dosyasındaki C# kaynak kodun içeriğini ve açıklamasını içerir. Bu dosyada bulunan L2XDBForm kısmi sınıfı üç mantıksal bölüme ayrılabilir: veri üyeleri ve `OnRemove` ve `OnAddBook` düğme olay işleyicileri ' ne tıklayın.

## <a name="data-members"></a>Veri üyeleri
 Bu sınıfı L2DBForm. xaml içinde kullanılan pencere kaynaklarıyla ilişkilendirmek için iki özel veri üyesi kullanılır.

- @No__t_0 ad alanı değişkeni `"http://www.mybooks.com"` başlatılır.

- Üye `bookList`, Oluşturucu içinde L2DBForm. xaml içindeki CDATA dizesine aşağıdaki satırla başlatılır:

    ```
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
    ```

## <a name="onaddbook-event-handler"></a>OnAddBook olay Işleyicisi
 Bu yöntem, aşağıdaki üç deyimi içerir:

- İlk koşullu ifade, giriş doğrulaması için kullanılır.

- İkinci ifade, kullanıcının **Yeni kitap** kullanıcı ARABIRIMI (UI) Ekle bölümünde girdiği dize değerlerinden yeni bir <xref:System.Xml.Linq.XElement> oluşturur.

- Son ifade, bu yeni kitap öğesini L2DBForm. xaml içindeki veri sağlayıcısına ekler. Sonuç olarak, dinamik veri bağlama Kullanıcı arabirimini bu yeni öğe ile otomatik olarak güncelleştirir; Ek Kullanıcı tarafından sağlanan kod gerekmez.

## <a name="onremove-event-handler"></a>OnRemove olay Işleyicisi
 @No__t_0 işleyicisi iki nedenden dolayı `OnAddBook` işleyicisinden daha karmaşıktır. İlk olarak, Ham XML korunmuş boşluk içerdiğinden, newlines ile eşleşen bir kitap girişi de kaldırılmalıdır. İkincisi, bir kolaylık olması halinde, silinen öğede bulunan seçim, listedeki bir öncekine sıfırlanır.

 Ancak, seçili kitap öğesini kaldırmanın temel çalışması yalnızca iki deyim tarafından gerçekleştirilir:

- İlk olarak, liste kutusunda şu anda seçili olan öğeyle ilişkili kitap öğesi alınır:

  ```
  XElement selBook = (XElement)lbBooks.SelectedItem;
  ```

- Ardından, bu öğe veri sağlayıcısından silinir:

  ```
  selBook.Remove();
  ```

  Dinamik veri bağlama, programın Kullanıcı arabiriminin otomatik olarak güncelleştirilmesini sağlar.

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

### <a name="code"></a>Kod

```csharp
using System;
using System.Linq;
using System.Collections;
using System.Collections.Generic;
using System.Diagnostics;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Input;
using System.Xml;
using System.Xml.Linq;

namespace LinqToXmlDataBinding {
    /// <summary>
    /// Interaction logic for L2XDBForm.xaml
    /// </summary>

    public partial class L2XDBForm : System.Windows.Window
    {
        XNamespace mybooks = "http://www.mybooks.com";
        XElement bookList;

        public L2XDBForm()
        {
            InitializeComponent();
            bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
        }

        void OnRemoveBook(object sender, EventArgs e)
        {
            int index = lbBooks.SelectedIndex;
            if (index < 0) return;

            XElement selBook = (XElement)lbBooks.SelectedItem;
            //Get next node before removing element.
            XNode nextNode = selBook.NextNode;
            selBook.Remove();

            //Remove any matching newline node.
            if (nextNode != null && nextNode.ToString().Trim().Equals(""))
            { nextNode.Remove(); }

            //Set selected item.
            if (lbBooks.Items.Count > 0)
            {  lbBooks.SelectedItem = lbBooks.Items[index > 0 ? index - 1 : 0]; }
        }

        void OnAddBook(object sender, EventArgs e)
        {
            if (String.IsNullOrEmpty(tbAddID.Text) ||
                String.IsNullOrEmpty(tbAddValue.Text))
            {
                MessageBox.Show("Please supply both a Book ID and a Value!", "Entry Error!");
                return;
            }
            XElement newBook = new XElement(
                                mybooks + "book",
                                new XAttribute("id", tbAddID.Text),
                                tbAddValue.Text);
            bookList.Add("  ", newBook, "\r\n");
        }
    }
}

```

### <a name="comments"></a>Açıklamalar
 Bu işleyiciler için ilişkili XAML kaynağı için bkz [. L2DBForm. xaml kaynak kodu](../designers/l2dbform-xaml-source-code.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Izlenecek yol: LinqToXmlDataBinding örneği](../designers/walkthrough-linqtoxmldatabinding-example.md) [L2DBForm. xaml kaynak kodu](../designers/l2dbform-xaml-source-code.md)
