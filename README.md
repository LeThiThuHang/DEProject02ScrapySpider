# DEProject02ScrapySpider

Bài toán: Sau khi bitcoin và các đồng tiền ảo sụt giảm, công ty có nhu cầu khảo sát thông tin về card đồ họa thông qua một website. Yêu cầu team Data Engineer collect và thống kê các thông tin tại danh mục trên website: [https://www.newegg.com](https://www.newegg.com/GPUs-Video-Graphics-Cards/SubCategory/ID-48?Tid=7709) để phía đội kinh doanh có cơ sở triển khai chiến dịch mới.

Mô tả cụ thể:

- Nguồn dữ liệu cần crawl là danh mục sau: https://www.newegg.com/GPUs-Video-Graphics-Cards/SubCategory/ID-48?Tid=7709
- Thông tin cần lấy:
    - ItemID
    - Title
    - Branding (Hãng)
    - Rating
    - Số lượng Rating
    - Price (Current Price) → Chuyển đổi dưới dạng number
    - Shipping (Free, Ko ship, hay mất phí)
    - Image URL
    - Các thông tin chi tiết về sản phẩm:
        - Max Resolution
        - DisplayPort
        - HDMI
        - DirectX
        - Model
     
    Use Scrapy framework to scrawl the data from website:
1. Setup scrapy : pip install scrapy
2. Create scrapy project: scrapy startproject newegg
3. Define a spider as skuspider.py
   navigate to the folder of the scrapy proejct
   create a new spider: scrapy genspider spider_name website_url (spider_name is skuspider file, website_url is https://www.newegg.com/GPUs-Video-Graphics-Cards/SubCategory/ID-48)
4. Define an item in the items.py
   define the class NeweggItem with the fields 
5. In the skupsider.py
   define the class SkuspiderSpider to scrape data from the list of url to the corresponding items field
6. In the pipeline.py
   define the transformation class to transform the fields in the items:
       class RatingTransform, class NumberRatingTransform, class ShipTransfrom
   define the NeweggPipeline includes:
     init function
     open_spider function
     close_spide function to write inforamtion to the 'data.csv'
     process_item function to apply the transformation class to the items
7. In the settings.py
   uncomment the ITEM_PIPELINES row to run the pipelines
8. In the terminal, in the scrapy spider folder, run the command: scrapy crawl skuspider
9. Check the data.csv and run the analysis
     


  
