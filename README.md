<strong>Herhangi uygulamamızda kullanılan servisler arka planda çalışır durumda olmasına rağmen kendisine gelen request’leri handle edemeyebilir. (Örneğin veritabanı bağlantısının kaybolması) Bu gibi durumlarda uygulamanın unhealthy duruma gelmesine neden olan sorunu tespit etmek gerekiyor. İmdadımıza yazımızın da konusu olan <em>health check</em> mekanizmaları koşuyor.</strong>



![](https://www.linkpicture.com/q/indir_15.png)



       // This method gets called by the runtime. Use this method to add services to the container.
    public void ConfigureServices(IServiceCollection services)
    {
       services.AddControllers();
       services.AddHealthChecks();
    }
       // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
     public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
       app.UseRouting();
       app.UseHealthChecks("/hc"); 
       app.UseEndpoints(endpoints => {endpoints.MapControllers();});
    }
