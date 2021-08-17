# rails-blog
  —-My rails project———
The project is about creating a physician office where the user can make an appointment within the list of physicians or make an appointment with a new physician.
When we first start a project, the most important thing to do is go over the relationships that the Models will have.
Now here we can see how my model/class will interact with each other.

The models
class User < ApplicationRecord
    has_many :physicians

class physician < ActiveRecord::Base
      has_many :appointments
      has_many :user, through; :appointments
end
class Appointment < ApplicationRecord
     belongs_to :physician
     belongs_to :category
End
class Category < ApplicationRecord
    has_many :appointments
    has_many :physicians, through: :appointments
End

The database

I used a Rails "generator", which creates and fills in a bunch of files so I don't have to. I generated appointments, users and categories, models, controller, views, and a physician.

 The model physician has two attributes, name and email. Both of these attributes are of type text building 
Our appointments table should have a column called date to represent the date and time the appointment will take place. 
The category table has just a name attributes (pediatricians)
The user can be a doctor or a patient looking for the appointment or doctor name and email
User has name , email  and password to open the app

I’ve provided a seed file so I can have some data to play around with –– run rails db:seed once your migrations and models are complete.
u1= User.create(username: "Jone", email: "jone@jone.com", password: "Jon")

 I typed $ rails db:rollback  when I made mistake with db and the last series of migrations that you ran will be reversed and I will be  back to where I was. Then I just edit the file, rerun the migrations, 

Controler
   
		I create a physician #shaw, #index, #create routes and controller the page that displays the physicians’s name,  and appointments, with each appointment's date, time, and user name is linking 
		I create a appointment#show , #index, #create page that lists the date and time for each of their appointments and links to category page.
	I create a user #index page that displays a link to each user’s show page and the appointments they have.

Validation

Validations are used to ensure that only valid data is saved into database.I Validate each models. Let’s say you want to make sure a username is unique
what happens if two users almost simultaneously submit the same username and it is received by two separate concurrent instances of your application?
 On User module validates :email, presence: true, uniqueness: true

 All the steps that require to build the application are
1. To establish relationship between the models
2. Validate the models
3. Establish and build complex form including the nested routes
4. Contract partial  using helper
Once you do this, we can see view in our server using rails s


What app  is doing is allowing our classes to communicate with each other. It 
show how information will be stored. Active record lets our code know that a user can know about their appointments and the  physicians 