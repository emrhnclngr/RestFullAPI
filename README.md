# RestFullAPI



    SOAP (Simple Object Access Protocol) uygulamalar ile web servislerin bilgi aktarımını sağlayan XML tabanlı bir protokoldür. Yani web servise giden bilgi XML olarak gönderilir, web servis bu bilgiyi yorumlar ve sonucunu XML olarak geri döndürür. SOAP tabanlı bir web servisin, gönderilen XML verisini nasıl yorumlayacağının tanımlanması gerekir. Bu web servis tanımlaması WSDL standardı ile yapılır.

    REST mimarisinde ise işlemler resource kavramıyla yapılır. Resource URI ile tanımlanır ve bir metod tanımlaması veya bir değişken olabilir. Yani REST’te SOAP’ta olduğu gibi XML yardımıyla metodlar çağırılmaz bunun yerine o metodu çağıracak URIler ile web servise HTTP protokolüyle istek yapılır. Böylece REST için WSDL gibi bir tanımlama diline ihtiyaç kalmaz işlemler tamamen HTTP metodları üzerinden yapılır. Örneğin, bir web servisin metodunu SOAP ile “getProductName” şeklinde çağırırken REST ile “/products/name/1″ URI’si ile çağırabiliriz. Ayrıca RESTin döndürdüğü veri tipinin de XML olması zorunlu değildir JSON, XML, TXT, HTML gibi istenen veri türünde değer döndürülebilir.


    REST-SOAP Avantajları

    1)SOAP XML veri tipini desteklerken REST istenen veri türüyle işlem yapabilir. JSON veri tipi ile XML’den çok daha düşük boyutlarla veri tutulabildiği için REST ile daha hızlı işlem yapılabilir.
    2)Ayrıca SOAP için WSDL ile tanımlama yapmak gerekirken REST için böyle bir zorunluluk yoktur. (WADL REST için kullanılan WSDL’e benzer bir yapıdır fakat kullanma zorunluluğu yoktur.) Bir dile ihtiyaç duymadan HTTP metodlarıyla tasarlanabildiği için REST’i kullanması ve tasarlaması daha kolaydır.
    3)SOAP için birçok geliştirme aracı mevcuttur, REST için geliştirme araçlarına ihtiyaç duyulmaz, tasarlaması kolaydır.
    4)SOAP; XML-Scheme kullanırken REST; URI-scheme kullanır yani metotlar için URI’ler tanımlanır.
    5)Her ikisi de HTTP protokolünü kullanırlar. Fakat REST için HTTP zorunluluğu varken SOAP; TCP, SMTP gibi başka protokollerle de çalışabilir.
    6)Test ve hata ayıklama aşaması REST için daha kolaydır. Çünkü HTTP hatalarını döndürür ve bunlar bir toola ihtiyaç duyulmadan görülebilir. SOAP için hata ayıklama araçları gerekebilir.
    7)REST basit HTTP GET metodunu kullandığı için cacheleme işlemi daha kolaydır. SOAP ile cacheleme yapabilmek için karmaşık XML requestleri yapılmalıdır.
    8)İkisi de HTTPS destekler, SOAP için WS-SECURITY adlı bir eklenti mevcuttur.
    9)Güvenlik açısından SOAP daha gelişmiştir çünkü hazır yapılar bulunmaktadır.
    10)Dokümantasyon bakımından SOAP daha gelişmiştir ve daha fazla kaynak bulunmaktadır.


    HTTP STATUS CODE :
    
    tarayıcıdan web server ' a bir servis isteği gönderildiğinde, hata meydana gelmesi mühtemeldir. Aşağıdaki kodlar HTTP durum kodları olarak client a gönderilebilir.

    Aşaağıda genelde karşılaşılan status kodlara değinilecektir.

    1xx: Information

    100 Continue : Sunucuyu request header alınmış ve istemci request body işlemek için göndermesi gerektiği durumunda oluşan bilgilendirme kodu

    2xx: Successful

    200 OK : başarılı HTTP isteklerinde oluşan başarı durum mesajı
    201 Created : sunucuda yeni bir kaynak oluşturulduğunda gönderilen başarı durum mesajı
    202 Accepted : sunucu gelen isteği kabul etti fakat işlem henuz tamamlanmadığında gönderilen başarı durum mesajı
    204 No Content	istek başarılı bir şekilde işlendi fakat her hangi bir içerik döndürülmedi 

    3xx: Redirection

    301 Moved Permanently	isteğin yapıldığı sayfa başka bir url taşınmış
    303 See Other	sayfaya yapılan istek başka urller altında da bulunabilir.
    302 Found	istek yapılan kaynak geçici olarak yeni bir url'e taşındı

    4xx: Client Error

    400 Bad Request	istek yapılan kaynak URL de yazım hatası olabilir.
    401 Unauthorized istek yapılan kayanağa erişim yetkisi yok
    404 Not Found	istek yapılan kaynak bulunamadı
    405 Method Not Allowed	istek yapılan kaynak metod erişimini desteklemiyor (get,post)
    410 Gone	istek yapılan kaynağa erişilemiyor. şuan erişim dışı. aslında kaynak var ama kaynağa erişimde sıkıntı söz konusu
    414 Request-URI Too Long istek yapılan kayanağa ait URI çok uzun olduğundan istek kabul edilmedi.

    415 Unsupported Media Type sunucu kaynağa yapılan isteği kabul etmiyor çünki desteklenen media format tipi bulunamadı xml olrak dışarı açılmış bir uri ye json formatter da ulaşırken alabileceğimiz bir hata

    5xx: Server Error

    500 Internal Server Error sunucuda bir exception hata oluştu. Genelde run-time da alınan hatalarda dönen bir sunucu durum hata mesajı

    511 Network Authentication Required	kullanıcılar ağ üzerinden kimlik doğrulaması yapmalıdır.

    503 Service Unavailable	sunucu down olmuş.

    505 HTTP Version Not Supported : sunucu HTTP protocol versiyonunu desteklemiyor.

    HTTP Methodları

    Method	Description
    HEAD	Get isteği gibi çalışır fakat sadece HTTP Header bilgisi taşır, content yok 
    PUT	    Varolan bir URI'deki veri yüklemek amaçlı kullanılır. UPDATE GET İşlemi
    DELETE	belirtilmiş bir kaynağı sunucundan kaldırır
    OPTIONS	Sunucu tarafından izin verilen HTTP methodların bilgisini verir
    CONNECT TCP/IP 	Converts the request connection to a transparent TCP/IP tunnel
