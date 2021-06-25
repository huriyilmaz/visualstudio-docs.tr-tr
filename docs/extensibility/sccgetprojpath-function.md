---
description: Bu işlev, kullanıcıdan yalnızca kaynak denetimi eklentisi için anlamlı olan bir dize olan bir proje yolu istemi gönderir.
title: SccGetProjPath İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 93266464249b8de037a618bab55ede31988384cb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901077"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath işlevi
Bu işlev, kullanıcıdan yalnızca kaynak denetimi eklentisi için anlamlı olan bir dize olan bir proje yolu istemi gönderir. Kullanıcı şu olduğunda çağrılır:

- Yeni proje oluşturma

- Sürüm denetimine mevcut bir projeyi ekleme

- Mevcut sürüm denetimi projesini bulmaya çalışma

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccGetProjPath (
   LPVOID pvContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPSTR  lpProjName,
   LPSTR  lpLocalPath,
   LPSTR  lpAuxProjPath,
   BOOL   bAllowChangePath,
   LPBOOL pbNew
);
```

### <a name="parameters"></a>Parametreler
 pvContext

[in] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[in] Kaynak denetimi eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 lpUser

[in, out] Kullanıcı adı (NULL sonlandırıcı dahil SCC_USER_SIZE için)

 lpProjName

[in, out] IDE projesinin, proje çalışma alanının veya makefile'ın adı (NULL sonlandırıcı dahil olmak SCC_PRJPATH_SIZE aşmama).

 lpLocalPath

[in, out] Projenin çalışma yolu. ise, kaynak denetimi eklentisi bu dizeyi değiştirebilir `bAllowChangePath` `TRUE` (null-sonlandırıcı dahil _MAX_PATH aşmamalıdır).

 lpUxProjPath

[in, out] Döndürülen proje yolu (NULL sonlandırıcı dahil olmak üzere SCC_PRJPATH_SIZE için bir arabellek.

 bAllowChangePath

[in] Bu `TRUE` ise, kaynak denetimi eklentisi dizeyi istendiğinde ve `lpLocalPath` değiştirebilir.

 pbNew

[in, out] Gelen değer, yeni bir proje oluşturulıp oluşturul olmadığını gösterir. Döndürülen değer, proje oluşturmanın başarılı olduğunu gösterir:

|Gelen|Yorum|
|--------------|--------------------|
|TRUE|Kullanıcı yeni bir proje oluşturabilir.|
|FALSE|Kullanıcı yeni bir proje oluşturmaz.|

|Giden|Yorum|
|--------------|--------------------|
|TRUE|Yeni bir proje oluşturuldu.|
|FALSE|Mevcut bir proje seçildi.|

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Proje başarıyla oluşturuldu veya alındı.|
|SCC_I_OPERATIONCANCELED|İşlem iptal edildi.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya sorun sorun nedeniyle kaynak denetim sistemine erişilirken bir sorun vardı.|
|SCC_E_CONNECTIONFAILURE|Kaynak denetim sistemine bağlanmaya çalışırken bir sorun vardı.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen bir hata oluştu.|

## <a name="remarks"></a>Açıklamalar
 Bu işlevin amacı, IDE'nin ve parametrelerini elde `lpProjName` `lpAuxProjPath` etmektir. Kaynak denetimi eklentisi kullanıcıdan bu bilgileri İstedikten sonra bu iki dizeyi IDE'ye geri iletir. IDE, bu dizeleri çözüm dosyasında kalıcı olarak bulundurarak kullanıcı bu projeyi her açtığında [SccOpenProject'e](../extensibility/sccopenproject-function.md) iletir. Bu dizeler, eklentinin bir projeyle ilişkili bilgileri izlemesini sağlar.

 İşlev ilk çağrıldında boş `lpAuxProjPath` bir dizeye ayarlanır. `lProjName` boş da olabilir veya kaynak denetimi eklentisinin kullanabileceği veya yoksayymak için IDE proje adını içerebilir. İşlev başarıyla döndür geldiğinde, eklenti karşılık gelen iki dizeyi döndürür. IDE bu dizeler hakkında varsayımda bulunamaz, bunları kullanmaz ve kullanıcının bunları değiştirmesine izin vermez. Kullanıcı ayarları değiştirmek isterse, IDE önceki sefer aldığı değerlerin aynısını geçerek `SccGetProjPath` yeniden çağıracak. Bu, eklentinin bu iki dize üzerinde tam denetime sahip olduğunu sağlar.

 için, IDE bir kullanıcı adı veya boş bir `lpUser` dize işaretçisi iletir. Bir kullanıcı adı varsa, kaynak denetimi eklentisi varsayılan olarak kullanmalıdır. Ancak, hiçbir ad geçirilemediyse veya oturum açma işlemi verilen adla başarısız olursa, eklenti kullanıcıdan oturum açma bilgilerini ister ve geçerli bir oturum açma bilgileri aldığında adı `lpUser` geri geçirsin. Eklenti bu dizeyi değiştirene kadar, IDE her zaman boyutta bir arabellek ayırır ( `SCC_USER_LEN` +1).

> [!NOTE]
> IDE'nin gerçekleştirdiği ilk eylem, işleve veya `SccOpenProject` işleve yapılan bir çağrı `SccGetProjPath` olabilir. Bu nedenle her iki parametre de aynı parametreye sahip olur ve bu parametre kaynak denetimi eklentisinin kullanıcının her ikisinde `lpUser` de oturum açması için kullanılabilir. İşlevden gelen dönüş bir hata gösteriyor olsa bile, eklentinin bu dizeyi geçerli bir oturum açma adıyla doldurması gerekir.

 `lpLocalPath` , kullanıcının projeyi tutan dizindir. Boş bir dize olabilir. Şu anda tanımlanmış bir dizin yoksa (bir kullanıcının kaynak denetim sisteminden bir projeyi indirmeye çalışması durumunda) ve ise, kaynak denetim eklentisi kullanıcıdan giriş ister veya içine kendi dizesini yer alan başka bir yöntem `bAllowChangePath` `TRUE` `lpLocalPath` kullanabilir. ise, kullanıcı zaten belirtilen dizinde çalıştığı için eklenti `bAllowChangePath` `FALSE` dizesini değiştirmemeli.

 Kullanıcı kaynak denetimi altına konacak yeni bir proje oluşturursa, kaynak denetimi eklentisi o anda kaynak denetim sisteminde bunu `SccGetProjPath` oluşturmaz. Bunun yerine, için sıfır olmayan bir değerle birlikte dizeyi geri iletir ve projenin kaynak `pbNew` denetim sisteminde oluşturulacak olduğunu belirtmektedir.

 Örneğin, Visual Studio'daki Yeni  Proje sihirbazında bulunan bir kullanıcı projesini kaynak denetimine eklerse Visual Studio bu işlevi çağırarak eklenti, Visual Studio projesini içermesi için kaynak denetim sisteminde yeni bir proje oluşturmanın uygun olup olmadığını belirler. Kullanıcı sihirbazı **tamamlamadan önce** İptal'e tıklarsa proje hiçbir zaman oluşturulmaz. Kullanıcı Tamam **'a** tıklarsa, Visual Studio çağırarak ve iletir ve o `SccOpenProject` anda kaynak `SCC_OPT_CREATEIFNEW` denetimli proje oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
