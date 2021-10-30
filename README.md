# Consultation_app

Used template to set up all

###
add in gem file:
gem 'simple_calendar', '~> 2.3'
gem 'trix', '~> 0.9.9'
gem 'stripe', '~> 4.0', '>= 4.0.2'
###

rails g scaffold Meeting name start_time:datetime end_time:datetime user:references
un-comment gem 'redis', '~> 4.0'
bundle install
delete scaffold.scss in assets/stylesheets

###
in stylesheets/application.scss add:
/*
*= require simple_calendar
*= require trix
*= require_tree .
*/
###

###
in application.js add:
//require trix
//require_tree . (?????)
###

rails g simple_calendar:views

###
in meetings controller:
add: before_action :authenticate_user!
index: @meetings = Meeting.all => @meetings = current_user.meetings.all
create: add @meeting.user_id = current_user.id
