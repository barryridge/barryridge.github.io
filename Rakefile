# Rakefile

require 'yaml'
require 'digest/md5'
require 'rmagick'
require 'open-uri'

namespace :assets do
  desc "Generate favicons using your Gravatar"
  task :favicons do
    config = YAML.load_file('_config.yml')
    gravatar_email = config['author']['email']
    asset_path = 'public'
    name_pre = "apple-touch-icon-%dx%d-precomposed.png"

    puts "Assembling Gravatar URL..."
    gravatar_hash = Digest::MD5.hexdigest(gravatar_email)
    gravatar_url = "http://www.gravatar.com/avatar/#{gravatar_hash}?s=144"

    origin = "origin.png"
    File.delete origin if File.exist? origin

    puts "Fetching Gravatar image..."
    open(origin, 'wb') do |file|
      file << open(gravatar_url).read
    end

    FileList["*apple-touch-ico*.png"].each do |img|
      File.delete img
    end

    FileList["*favicon.ico"].each do |img|
      File.delete img
    end

    [144, 114, 72, 57, 32].each do |size|
      im = Magick::Image::read(origin).first.resize(size, size)
      circle = Magick::Image.new size, size
      gc = Magick::Draw.new
      gc.fill 'black'
      gc.circle size/2, size/2, size/2, 1
      gc.draw circle
      mask = circle.blur_image(0,1).negate
      mask.matte = false
      im.matte = true
      im.composite!(mask, Magick::CenterGravity, Magick::CopyOpacityCompositeOp)
      if size > 32
        puts "Generating #{name_pre} icon..." % [size, size]
        im.write "#{asset_path}/" + name_pre % [size, size]
      else
        puts "Generating favicon.ico..."
        im.write "#{asset_path}/favicon.ico"
      end
    end

    puts "Cleaning up..."
    File.delete origin
  end
end
