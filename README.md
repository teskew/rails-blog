# rails-blog
  My rails project
The project is about physician office where user can make an appointment  within the list of doctors  or can make an appointment with new doctor.
* We used a Rails "generator", which creates and fills in a bunch of files so we don't have to.
* We generated a physician, appointments, users and categories models  which includes a controller, and views, 
Before seeing what Rails has put together, run rails db:migrate again. This will set up the physician model in the database. We made a model called physician that has two attributes, name and email. Both of these attributes are of type text building an app for keeping physician. i need a physician model,

class Physician < ApplicationRecord
    belongs_to :user
    has_many :appointments
    has_many :categories, through: :appointments
     validates :name, presence: true 
    validates :email, presence: true
end

 the physiciansController
def create
        @physician= current_user.physicians.build(physician_params)
        if @physician.save
            redirect_to physician_path(@physician)
        else
            render :new
        end
    end

 so we can see our physicians in our browser, and views for our controller to render. 

<%= form_for([@physician, @appointment]) do |f| %>
   <%= f.hidden_field :physician_id %>
    <%= f.label :date %>
     <%= f.datetime_field :date %><br/>

 The steps that require to build the application 
1. To establish relationship between the models
2. Validate the models
3. Establish and build complex form including the nested routes
4. Contract partial  using helper
Once you do this, we can see  in our server using rails s
