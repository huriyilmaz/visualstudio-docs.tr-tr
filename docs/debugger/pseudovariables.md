---
title: Sözde değişkenler | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b6856517a680809ccc802c02dc880b6349eadc5
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535954"
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısında sahte değişkenler
Sözde değişkenler, belirli bilgileri bir değişken penceresinde veya **QuickWatch** iletişim kutusunda göstermek için kullanılan terimlerdir. Bir sözde değişkeni, normal bir değişkene girebileceğiniz şekilde girebilirsiniz. Ancak sözde değişkenler, değişken değildir ve programınızdaki değişken adlarına karşılık gelmez.

## <a name="example"></a>Örnek
 Bir yerel kod uygulaması yazdığınızı ve uygulamanızda ayrılan tanıtıcı sayısını görmek istediğinizi varsayalım. **Gözcü** penceresinde, **ad** sütununa aşağıdaki sözde değişkeni girebilir ve sonra değerlendirmek için Return tuşuna basabilirsiniz:

`$handles`

 Yerel kodda, aşağıdaki tabloda gösterilen sözde değişkenleri kullanabilirsiniz:

|Sözde değişken|İşlev|
|--------------------|--------------|
|`$err`|SetLastError işleviyle birlikte ayarlanan son hata değerini görüntüler. Görüntülenen değer, GetLastError işlevinin ne döndürüleceğini gösterir.<br /><br /> Bu değerin kodu çözülmüş biçimini görmek için `$err,hr` kullanın. Örneğin, son hata 3 ise `$err,hr` görüntülenir `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|
|`$handles`|Uygulamanızda ayrılan tanıtıcı sayısını görüntüler.|
|`$vframe`|Geçerli yığın çerçevesinin adresini görüntüler.|
|`$tid`|Geçerli iş parçacığının iş parçacığı KIMLIĞINI görüntüler.|
|`$env`|Dize görüntüleyicisinde ortam bloğunu görüntüler.|
|`$cmdline`|Programı başlatan komut satırı dizesini görüntüler.|
|`$pid`|İşlem KIMLIĞINI görüntüler.|
|`$` *RegisterName*<br /><br /> veya<br /><br /> `@` *RegisterName*|Kayıt *RegisterName*'in içeriğini görüntüler.<br /><br /> Normalde kayıt adını girerek kayıt içeriğini görüntüleyebilirsiniz. Bu söz dizimini kullanmanız gereken tek zaman, YAZMAÇ adının bir değişken adını aşırı yükleyidir. Kayıt adı, geçerli kapsamdaki bir değişken adıyla aynıysa, hata ayıklayıcı adı değişken adı olarak yorumlar. Bu, `$`*RegisterName* veya `@`*RegisterName* 'in yararlı olduğu durumlarda vardır.|
|`$clk`|Saat döngülerinde saati görüntüler.|
|`$user`|Uygulamayı çalıştıran hesap için hesap bilgilerine sahip bir yapı görüntüler. Güvenlik nedenleriyle parola bilgileri gösterilmez.|
|`$exceptionstack`|Geçerli Windows Çalışma Zamanı özel durumunun yığın izlemesini görüntüler. `$ exceptionstack` yalnızca UWP uygulamalarında kullanılabilir. `$ exceptionstack`, ve SEH özel C++ durumları için desteklenmez|
|`$returnvalue`|Bir .NET yönteminin dönüş değerini görüntüler.|

 ' C# De, aşağıdaki tabloda gösterilen sözde değişkenleri kullanabilirsiniz:

|Sözde değişken|İşlev|
|--------------------|--------------|
|`$exception`|Son özel durum hakkındaki bilgileri görüntüler. Hiçbir özel durum oluştuysa, değerlendirme `$exception` bir hata mesajı görüntüler.<br /><br /> Özel durum Yardımcısı devre dışı bırakıldığında, bir özel durum oluştuğunda `$exception` **Yereller** penceresine otomatik olarak eklenir.|
|`$user`|Uygulamayı çalıştıran hesap için hesap bilgilerine sahip bir yapı görüntüler. Güvenlik nedenleriyle parola bilgileri gösterilmez.|
|`$returnvalue`|Bir .NET yönteminin dönüş değerini görüntüler.|

 Visual Basic, aşağıdaki tabloda gösterilen sözde değişkenleri kullanabilirsiniz:

|Sözde değişken|İşlev|
|--------------------|--------------|
|`$exception`|Son özel durum hakkındaki bilgileri görüntüler. Hiçbir özel durum oluştuysa, değerlendirme `$exception` bir hata mesajı görüntüler.|
|`$delete` veya `$$delete`|**Komut** penceresinde oluşturulan örtük bir değişkeni siler. Söz dizimi `$delete,` *değişken* veya `$delete,` *değişkenidir* `.`|
|`$objectids` veya `$listobjectids`|Tüm etkin nesne kimliklerini belirtilen ifadenin alt öğesi olarak görüntüler. Söz dizimi `$objectid,` *ifade* veya `$listobjectids,` *ifade* `.`|
|`$` *N* `#`|Nesne KIMLIĞIYLE birlikte *N*değerine eşit olan nesneyi görüntüler.|
|`$dynamic`|@No__t_1 uygulayan bir nesne için özel **Dinamik görünüm** düğümünü görüntüler. Arayüz. Söz dizimi `$dynamic,` *nesnesidir*. Bu özellik yalnızca .NET Framework sürüm 4 veya üstünü kullanan kod için geçerlidir.|

## <a name="see-also"></a>Ayrıca Bkz.
- [İzleme ve Hızlı İzleme Pencereleri](../debugger/watch-and-quickwatch-windows.md)
- [Değişken pencereleri](../debugger/debugger-windows.md)
