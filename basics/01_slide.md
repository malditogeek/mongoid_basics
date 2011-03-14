!SLIDE
# Mongoid

!SLIDE bullets incremental transition=fade
# ODM for MongoDB

* (Pretty) slim
* Performant
* Feature rich *
* Well documented
* Built on top of mongo-ruby-driver

!SLIDE bullets incremental transition=scrollUp
# ActiveModel <3

* Validation support
* Callbacks for certain operations
* Making objects serializable
* Tracking value changes
* Observer support
* Adding +errors+ interface to objects

!SLIDE code transition=fade

	@@@ Ruby
	class Product 
	  include Mongoid::Document
	  field :title
	  field :url
	  field :sku
	
	  validates_presence_of :title
	  validates_uniqueness_of :sku
	  validates_format_of :url, :with => /^https?:\/\//
	
	  after_create :scrape
	
	  def scrape
	   do_something
	  end
	end

	Product.create/save({}) # Fail silently
	Product.create!/save!({}) # Raise exception

!SLIDE bullets incremental transition=scrollUp
# Give me more!

* Type coercion
* Document embedding (Associations)
* Criteria API
* Inheritance
* Indexing

!SLIDE code transition=fade

	@@@ Ruby
	class Product
	  include Mongoid::Document
	  field :last_price_update, :type => Date
	  field :countries, :type => Array
	  field :sku
	
	  index :sku
	
	  embeds_many :retailers
	end

!SLIDE bullets incremental transition=scrollUp
# Extra coolness

* Master/Slave support
* Versioning
* Timestamping
* "Paranoid" documents
* Caching

!SLIDE transition=fade

	@@@ Ruby
	class Product
	  include Mongoid::Document
	  include Mongoid::Versioning
	  include Mongoid::Timestamps
	  
	  enslave
	  cache
	end

!SLIDE bullets transition=scrollUp
# Resources

* [Mongoid Docs](http://mongoid.org/docs/installation/)
* [Mongoid Code](https://github.com/mongoid/mongoid)
* [ActiveModel](https://github.com/rails/rails/tree/master/activemodel)
* [Mongo Ruby Driver](https://github.com/mongodb/mongo-ruby-driver)


