******************************** 1.G�n ********************************
-Blank Solution olu�turduk
-Katmanl� mimari i�in ilgili projeleri solutiona ekleme(Api(Asp .Net Core Api) - Core(Class Library) - Data(Class Library) - Mvc(Asp .Net Core Mvc)-Service(Class Library)


-Core katman�-
	-Model Klas�r� olusturduk.Ic�nde BaseEntity Category ve Product classlar�n� yazd�k.
	-Category ve product classlar�na BaseEntity class�n� miras verdik.
	-Bu classlar ayn� zamanda Db de tablolara d�n��ece�i i�in propertylerle doldurduk.
	-Product ve Category aras�ndaki foreign key ba�lant�s�n� navigation propertylerle sa�lad�k.

	-Repository klas�r�n� olu�turduk(Interface yap�lar� in�aa etmek i�in.)
	-IRepository de Crud i�lerimlerini tan�mladik.
	-ICategoryRepository de Category s�n�f� i�in ihtiyac�m�z olan db islemleri icin ayr�ca interface olu�turduk.
	-IProductRepository de Product s�n�f� i�in ihtiyac�m�z olan db islemleri icin ayr�ca interface olu�turduk.

	-Service klas�r� ekledik amac�m�z Api ve Mvc katmanlar�n�n Repository �zerinden de�il de service katman� �zerinden haberle�tirmek i�in.

	-UnitOfWork klas�r� db de nihai kay�t komutu olan SaveChange() komutunu Repositoryden ay�rarak crud i�lemleri ile kay�t aras�nda ihtiyac�m�z
	olmas� durumunda kod ekleme i�in kullanaca��z.



-Data Katman�-
	**Kullan�lan K�t�phaneler
	**Microsoft.EntityFrameworkCore
	**Microsoft.EntityFrameworkCore.Design
	**Microsoft.EntityFrameworkCore.SqlServer
	**Microsoft.EntityFrameworkCore.Tools


	-Projenin Context s�n�f�n� burada olu�turduk(AppDbContext) bu s�n�fa entityframeworkdeki DbContext() s�n�f�n� miras verdil

	-AppDbContext i�inde DbSet<> i�lemlerini ger�ekle�tirdik. Migration i�lemi ba�lad���nda classlar�m�z db'de Tablellara d�n��t�r�l�rken
	gerekli olan property ayarlar�n� onModelCreating metoduyla FluentApi kullanarak tablolar�m�z�n propertylerini d�zenledik
	
	-Dbde tablolar�m�z olu�tuktan sonra Seed metodunu kullanarak olu�an tablolara test datalar� y�kledik.

	-Context ile Db aras�ndaki ba�lant�y� Api katman� �zerindeki appsetting.json dosyas�n� kullanrak connectionstring ifadesini ekledik.


******************************** 2.G�n ********************************
-Api Katman�-
	**AutoMapper.Extensions.Microsoft.DependencyInjection

	-Dto dosyas�nda CategoryDto,ProductDto s�n�flar� eklenerek propertyler ve requiredlar yaz�ld�. CategoryWithProduct ve ProductWithCategory aras�nda navigasyon yaz�ld�.

	-Mapping Klas�r�ndeki MapProfile s�n�f� ile Dtolar�n Mapping i�lemi yap�ld�.

	-CategoryController eklenerek HttpGet(GetAll,GetById) metodlar� yaz�ld�.
	-Constructorda category service ve mapperlara atama yap�ld�.

-Data Katman�-

	-UnitOfWork class� eklenerek SaveChanges ve SaveChangesAsync eklendi.
	
-Service Katman�-

	-CategoryService class�nda Service<Category> ve ICategoryService'den miras ald�k.







